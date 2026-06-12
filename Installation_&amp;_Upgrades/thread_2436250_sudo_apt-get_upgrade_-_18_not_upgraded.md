---
title: "sudo apt-get upgrade - 18 not upgraded"
date: 2020-02-03
forum: Installation &amp; Upgrades
---

### Post by marchello_lippi2 on 2020-02-03
Hi all, 
Getting below message when trying to upgrade. How do I dig it deeper?
```

[FONT=monospace][COLOR=#000000]$ sudo apt-get upgrade[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  calendar-indicator libgl1-mesa-dri libgl1-mesa-dri:i386 libglapi-mesa libglapi-mesa:i386 libglx-mesa0 libglx-mesa0:i386 libodbc1 libosmesa6 libosmesa6:i386 libxatracker2 mesa-va-drivers mesa-vdpau-drivers unixodbc wine-stable
  wine-stable-amd64 wine-stable-i386:i386 winehq-stable
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
[/FONT]
```
```
[FONT=monospace][COLOR=#000000]$ lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:        18.04
Codename:       bionic
[/FONT]
```

---

### Post by guiverc on 2020-02-03
use `sudo apt-get dist-upgrade`

apt-get upgrade can only upgrade certain packages (ie. it has limits). From `man apt-get`

> dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing
           dependencies with new versions of packages; apt-get has a "smart" conflict resolution system, and it will
           attempt to upgrade the most important packages at the expense of less important ones if necessary. The
           dist-upgrade command may therefore remove some packages. The /etc/apt/sources.list file contains a list of
           locations from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for
           overriding the general settings for individual packages.

---

