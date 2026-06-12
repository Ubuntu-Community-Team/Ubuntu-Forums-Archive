---
title: "Can't report bugs because I have obsolete package versions installed ?"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DJ Barney on 2010-03-14
I get the bug report icon in the tray. A few report OK, but most I get this message ...

> The problem cannot be reported:

You have some obsolete package versions installed. Please upgrade the following packages and check if the problem still occurs:

libblkid1, libuuid1, util-linux

The package names vary. I did a clean install of the release pre Lucid and then I upgraded to Lucid from there. I don't remember any errors reported but I;m not sure where the upgrade logs are.

Any help appreciated. I would really like to report these bugs !

---

### Post by ssam on 2010-03-14
if you run update manager you will see upgrades for those packages.

---

### Post by NCLI on 2010-03-14
Or simply 'sudo apt-get update && sudo apt-get upgrade --yes'

---

### Post by kansasnoob on 2010-03-14
You can find apts history with:

```
cat /var/log/apt/history.log
```

If you want to check the current version of a specific package:

```
sudo apt-cache show <package-name>
```

eg, "util-linux":

```
sudo apt-cache show util-linux
```

> lance@lance-desktop:~$ sudo apt-cache show util-linux
[sudo] password for lance: 
Package: util-linux
Essential: yes
Priority: required
Section: utils
Installed-Size: 2208
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: LaMont Jones <lamont@debian.org>
Architecture: i386
**Version: 2.17-0ubuntu3**
Replaces: e2fsprogs (<= 1.41.8-1ubuntu1), fdisk, linux32, miscutils, schedutils, setterm, sparc-utils
Provides: linux32, schedutils
Depends: upstart-job, lsb-base (>= 3.0-6), tzdata (>= 2006c-2), dpkg (>= 1.15.4) | install-info
Pre-Depends: libblkid1 (>= 2.17), libc6 (>= 2.11), libncurses5 (>= 5.6+20071006-3), libselinux1 (>= 1.32), libslang2 (>= 2.0.7-1), libuuid1 (>= 2.16), zlib1g (>= 1:1.1.4)
Suggests: util-linux-locales, kbd | console-tools, dosfstools
Conflicts: console-tools (<< 1:0.2.3-21), fdisk, kbd (<< 1.05-3), linux32, schedutils, setterm
Breaks: udev (<< 136-1)
Filename: pool/main/u/util-linux/util-linux_2.17-0ubuntu3_i386.deb
Size: 531034
MD5sum: 69cdb002779e226655f3cfd7913cb271
SHA1: 09cf2b69828a7b6f5e180396d73eb945c13cf8ee
SHA256: fa869c4d6071989f93ffcdf97cdb8ff940b31a91a85119ba2ee38f73ed0aec3b
Description: Miscellaneous system utilities
 This package contains a number of important utilities, most of which
 are oriented towards maintenance of your system.  Some of the more
 important utilities included in this package allow you to partition
 your hard disk, view kernel messages, and create new filesystems.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Supported: 5y
Task: minimal


Synaptic can also be a real work horse for you. For instance you can use the Custom Filters to search for upgradeable upstream packages, you can search by package name, check your repos under Settings > Repositories, click on Reload and Mark all upgrades and then review what's upgradeable, etc.

---

### Post by DJ Barney on 2010-03-14
Thanks. I'll try those out :)

---

### Post by dinamic1 on 2010-03-14
i have the same problem but with udisks

[http://i43.tinypic.com/11rw2n4.png](http://i43.tinypic.com/11rw2n4.png)

---

### Post by teh603 on 2010-03-14
I'm having the problems with the parted and udisks packages as well. Were they supposed to be removed or something?

---

### Post by DoeRayMe on 2010-03-14
> **teh603 said:**
> I'm having the problems with the parted and udisks packages as well. Were they supposed to be removed or something?

That they wont upgrade? if so install libparted0 and it will remove the packages it needs and upgrades them

---

### Post by dinamic1 on 2010-03-15
> **NCLI said:**
> Or simply 'sudo apt-get update && sudo apt-get upgrade --yes'
Reading state information... Done
The following packages have been kept back:
  parted udisks
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by NCLI on 2010-03-15
Try doing what DoRayMe suggests and install libparted0 then.

---

