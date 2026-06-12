---
title: "Wolfenstein enemy territory"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by AngelOfMercy on 2010-11-04
Hey all, I been trying all night to install enemy territory and keep getting this error 

```

[sudo] password for admin:
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
./setup.sh: line 143: 26993 Aborted                 "$setup" "$@" 2>> $NULL
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

```i have tried 

$ sudo apt-get install libgtk1.2

```
Reading state information... Done
libgtk1.2 is already the newest version.
The following packages were automatically installed and are no longer required:
  binutils-static linux-restricted-modules-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```im still getting same error

i tried sudo apt-get update and get 404 error's

```
 [SIZE=1]404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) gutsy/all Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
  404 Not Found [IP: 91.189.92.170 80]
Err [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) gutsy/all Sources
  404 Not Found
Get: 2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_GB
Get: 3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 199B in 3s (63B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/gutsy/main/source/Sources.gz](http://wine.budgetdedicated.com/apt/dists/gutsy/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://ubuntu.iuculano.it/dists/gutsy/all/binary-i386/Packages.gz](http://ubuntu.iuculano.it/dists/gutsy/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.iuculano.it/dists/gutsy/all/source/Sources.gz](http://ubuntu.iuculano.it/dists/gutsy/all/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
admin@ks30499:~$ W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.170 80][/SIZE]


```im running 32 bit ubuntu 8.04 on dedicated server

---

### Post by stlsaint on 2010-11-04
> **AngelOfMercy said:**
> Hey all, I been trying all night to install enemy territory and keep getting this error 


i have tried 

$ sudo apt-get install libgtk1.2



im still getting same error

i tried sudo apt-get update and get 404 error's



im running 32 bit ubuntu 8.04 on dedicated server


Those 404 errors mean your sever is having connection issues. Check the network connectivity on the server then try update/dist-upgrade again.

---

### Post by AngelOfMercy on 2010-11-04
i can wget most things on it though :/ If it something to do with my bind well im lost there :(

---

### Post by oldos2er on 2010-11-04
> **AngelOfMercy said:**
> im running 32 bit ubuntu 8.04 on dedicated server

Gutsy (8.10) reached its end-of-life long ago. Your sources.list should be referencing Hardy (8.04) instead.

---

### Post by AngelOfMercy on 2010-11-04
could you please explain how to do that please

---

### Post by oldos2er on 2010-11-04
Can you confirm you're running 8.04? And if so, someone (?) must've changed sources.list from what it was originally.

In gedit, I would use Search, Advanced Find and Replace. In nano, use Ctrl-\

---

### Post by AngelOfMercy on 2010-11-04
Operating system	Ubuntu Linux 8.04
im new to this linux stuff. I mainly use ssh so i allways ran commands. if there is a command to install Hardy (8.04), and would i need to remove the older Gutsy (8.10)

---

### Post by AngelOfMercy on 2010-11-04
i tried this command (sudo apt-get install --reinstall libgtk1.2-common) and got the following.

> 
$ sudo apt-get install --reinstall libgtk1.2-common
[sudo] password for *****:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reinstallation of libgtk1.2-common is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  binutils-static linux-restricted-modules-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$


---

### Post by AngelOfMercy on 2010-11-04
i have tried removing it all together with command (sudo apt-get autoremove) and get the following

> $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  binutils-static linux-restricted-modules-common
The following packages will be REMOVED
  binutils-static linux-restricted-modules-common
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1487kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 108394 files and directories currently installed.)
Removing linux-restricted-modules-common ...
Removing binutils-static ...

Then i ran (sudo apt-get install --reinstall libgtk1.2-common)
and got the following
> $ sudo apt-get install --reinstall libgtk1.2-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reinstallation of libgtk1.2-common is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by oldos2er on 2010-11-04
When an Ubuntu release reaches end-of-life, its repositories no longer function, which is why apt-get isn't working. You'll need to edit /etc/apt/sources.list as I suggested earlier.

---

### Post by AngelOfMercy on 2010-11-04
yes i remember changing this :/ lol could you point me to a working on i could use so i can update and fix it please

---

### Post by AngelOfMercy on 2010-11-04
would this one be any good 
```
Sources.List For Ubuntu Hardy Heron (8.04)
## a &#8220;general&#8221; sources.list for Hardy Heron; all sources are uncommented.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the &#8216;backports&#8217;
## repository.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical&#8217;s
## &#8216;partner&#8217; repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
```

---

### Post by AngelOfMercy on 2010-11-04
i tried it anyways, I saw the problem that was, it was all setup for gutsy. i changed and used the new source but now im back to my 404 error but if im guessing right it because it still setyup for gutsy somewhere.
> Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
  404 Not Found [IP: 91.189.92.166 80]
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
  404 Not Found [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
  404 Not Found [IP: 91.189.92.171 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
  404 Not Found [IP: 91.189.92.171 80]


---

### Post by uRock on 2010-11-04
Have you tried the game's forums as well? [http://forumplanet.gamespy.com/planetwolfenstein](http://forumplanet.gamespy.com/planetwolfenstein) I am not sure how much of their forums are used for Linux, but thought it may be worth a try.

---

### Post by AngelOfMercy on 2010-11-04
ok hold on a mo so sorry i just double checked the source.list and it didnt save i tryin again. and all lookes good with suda apty-get update
> 
Fetched 9479kB in 20s (457kB/s)
Reading package lists... Done


---

### Post by AngelOfMercy on 2010-11-04
> **uRock said:**
> Have you tried the game's forums as well? [http://forumplanet.gamespy.com/planetwolfenstein](http://forumplanet.gamespy.com/planetwolfenstein) I am not sure how much of their forums are used for Linux, but thought it may be worth a try.
yeah i been searching for 30 hrs i searched everywhere. this problem seems to be a problem on my system not the game itself. since i changed source code the update worked for once

---

