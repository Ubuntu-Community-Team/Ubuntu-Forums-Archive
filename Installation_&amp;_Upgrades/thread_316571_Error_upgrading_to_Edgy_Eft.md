---
title: "Error upgrading to Edgy Eft"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by Rinulin on 2006-12-11
I receive the following error when I attempt to upgrade to 6.10:

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

It then lists the following items:

> cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


It appears that this is the original kernel that was installed with the operating system. I immediately upgraded to the 686 kernelafter installing Ubuntu. I tried to find these in Synaptic, but I haven't had any luck.

Any suggestions?

---

### Post by odinfromvalhalla on 2006-12-11
try this in a terminal:

sudo gedit /etc/apt/sources.list

there you should find the two lines the apt was yelling about:
```
cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
```

just add a # in front of each line and save the file.

try the upgrade again.

---

### Post by Rinulin on 2006-12-11
Thanks very much! That did the trick.

---

