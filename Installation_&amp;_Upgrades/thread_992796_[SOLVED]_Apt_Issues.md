---
title: "[SOLVED] Apt Issues"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by amarula on 2008-11-25
Hi Guys

I get the error below when I try to apt-get install any packages. I have been able to install before, and this issue started yesterday. Please assist if you can.

Err [ftp://za.archive.ubuntu.com](ftp://za.archive.ubuntu.com) hardy Release.gpg
  PASS failed, server said: Login incorrect.

---

### Post by Partyboi2 on 2008-11-25
If you don't need to use [ftp://za.archive.ubuntu.com]("ftp://za.archive.ubuntu.com/") remove it from your sources.list. Open a terminal (Applications>Accessories>Terminal)
```
gksu gedit /etc/apt/sources.list
``` then remove it or put a # infront of it, then save and back in a terminal ```
sudo apt-get update
```

---

### Post by JamesGarry on 2008-11-25
The follwing link has very clear instructions
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
 otherwise u can remove
[ftp://za.archive.ubuntu.com](ftp://za.archive.ubuntu.com) from the sources.list if u dont need this

---

### Post by amarula on 2008-11-25
thanks for your help so far guys. I have commented the problem server out now i get the following error using a different server.

Get:44 [ftp://ftp.is.co.za](ftp://ftp.is.co.za) hardy-updates/multiverse Sources
Err [ftp://ftp.is.co.za](ftp://ftp.is.co.za) hardy-updates/multiverse Sources
  Unable to fetch file, server said 'Failed to open file.  '
W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy/main/binary-i386/Packages.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy/main/source/Sources.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy/main/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy/restricted/source/Sources.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy/restricted/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy/universe/source/Sources.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy/universe/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy/multiverse/source/Sources.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy/multiverse/source/Sources.gz)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.is.co.za/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](ftp://ftp.is.co.za/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Failed to open file.  '

---

### Post by Partyboi2 on 2008-11-25
Can you open a terminal (Applications>Accessoires>Terminal) and post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by amarula on 2008-11-25
this is my sources list.

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
#deb [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy main restricted
#deb-src [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy main restricted
deb [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy main restricted
deb-src [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy main restricted
#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy main restricted
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

#deb [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy-updates main restricted
#deb-src [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy-updates main restricted
deb [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy-updates main restricted
deb-src [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy-updates main restricted
#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

#deb [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy universe
#deb-src [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy universe
#deb [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy-updates universe
#deb-src [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy-updates universe
deb [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy universe
deb-src [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy universe
deb [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy-updates universe
deb-src [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy-updates universe
#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy universe
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy universe
#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy-updates universe
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy multiverse
#deb-src [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy multiverse
#deb [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy-updates multiverse
#deb-src [ftp://mirror.ubuntu.ac.za/ubuntu/](ftp://mirror.ubuntu.ac.za/ubuntu/) hardy-updates multiverse
deb [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy multiverse
deb-src [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy multiverse
deb [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy-updates multiverse
deb-src [ftp://ftp.is.co.za/ubuntu/](ftp://ftp.is.co.za/ubuntu/) hardy-updates multiverse
#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy multiverse
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy multiverse
#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by linux_tech on 2008-11-25
Do you already have a backup of your original sources.list?
If you do then you could restore it by-
```
sudo cp /path/to/backup /etc/apt/sources.list
```

You should always make a backup before editing
```
sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak
```

---

### Post by amarula on 2008-11-25
thanks for all your support, i finally go it to work by using the following server. [ftp://ftp.sun.ac.za/ftp/ubuntu/](ftp://ftp.sun.ac.za/ftp/ubuntu/)

---

