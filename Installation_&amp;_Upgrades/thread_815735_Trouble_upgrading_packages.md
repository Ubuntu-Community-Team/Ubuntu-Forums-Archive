---
title: "Trouble upgrading packages"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by justinhj on 2008-06-01
I'm getting some errors when I run upgrade. Not sure how to track them down. Help would be greatly appreciated ;-)

```

justinhj@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnome-about gnome-desktop-data libgnome-desktop-2 libgnome-desktop-dev
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 917kB of archives.
After this operation, 12.3kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Err http://mirror.cpsc.ucalgary.ca hardy-updates/main gnome-about 1:2.22.2-0ubuntu1
  404 Not Found
Err http://mirror.cpsc.ucalgary.ca hardy-updates/main gnome-desktop-data 1:2.22.2-0ubuntu1
  404 Not Found
Err http://mirror.cpsc.ucalgary.ca hardy-updates/main libgnome-desktop-dev 1:2.22.2-0ubuntu1
  404 Not Found
Err http://mirror.cpsc.ucalgary.ca hardy-updates/main libgnome-desktop-2 1:2.22.2-0ubuntu1
  404 Not Found
Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/pool/main/g/gnome-desktop/gnome-about_2.22.2-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/pool/main/g/gnome-desktop/gnome-desktop-data_2.22.2-0ubuntu1_all.deb  404 Not Found
Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/pool/main/g/gnome-desktop/libgnome-desktop-dev_2.22.2-0ubuntu1_i386.deb  404 Not Found
Failed to fetch http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/pool/main/g/gnome-desktop/libgnome-desktop-2_2.22.2-0ubuntu1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

And source.list looks like 

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy main restricted
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-updates main restricted
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy universe
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy universe
deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-updates universe
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-updates universe

deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy multiverse
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy multiverse
deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-updates multiverse
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages hardy-updates multiverse

# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-security main restricted
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-security main restricted
deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-security universe
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-security universe
deb http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-security multiverse
deb-src http://mirror.cpsc.ucalgary.ca/mirror/ubuntu.com/packages/ hardy-security multiverse

# Gilir's screenlets 
deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe 

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free  

```

---

### Post by iaculallad on 2008-06-01
Try changing the "Download from" server to use "Main Server". System->Administration->Software Sources, under the "Ubuntu Software" tab then click on Close button. Redo upgrade.

---

### Post by justinhj on 2008-06-03
Thanks for pointing me to that, I'm good now. I followed your instructions but also had to uncheck all the calgary university mirrors in the 3rd Party software tab.

---

