---
title: "Strange updating probelm"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by Cochise on 2010-07-28
I'll start with explaining my setup. ASUS eeePC 2G Surf, / is mounted on the internal SSD (2GB) and /usr is on a 2GB SD Card. The OS is working and all the latest updates are done except I'm having trouble installing one upgrade package.OS is Ubuntu Netbook Remix 10.04.

Output of uname -r

> 2.6.32-24-generic

Output of df -h

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             1.9G  550M  1.3G  31% /
none                  239M  256K  238M   1% /dev
none                  245M  212K  245M   1% /dev/shm
none                  245M   84K  245M   1% /var/run
none                  245M     0  245M   0% /var/lock
none                  245M     0  245M   0% /lib/init/rw
/dev/sdb1             1.9G  1.4G  469M  75% /usr
/home/jshortland/.Private
                      1.9G  550M  1.3G  31% /home/jshortland


Output of sudo apt-get upgrade

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-headers-generic: Depends: linux-headers-2.6.32-24-generic but it is not installed
E: Unmet dependencies. Try using -f.

Output of sudo apt-get install -f

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-2.6.32-24-generic
The following NEW packages will be installed:
  linux-headers-2.6.32-24-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/740kB of archives.
After this operation, 9,191kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 123013 files and directories currently installed.)
Unpacking linux-headers-2.6.32-24-generic (from .../linux-headers-2.6.32-24-generic_2.6.32-24.38_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-24-generic_2.6.32-24.38_i386.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-2.6.32-24-generic/include/linux/shm.h': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.32-24-generic_2.6.32-24.38_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


The SD card (/usr) has 400MB free and / has 1GB free, that should be enough I thought. Any ideas guys?

---

### Post by Cochise on 2010-07-28
Ran sudo apt-get remmove linux-headers-generic solved the problem.

---

