---
title: "Problem upgrading libc6-686 [gutsy]"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by FarJumper on 2007-09-19
During the latest upgrade my libc6-i686 want to be removed and be
replaced with newer version libc6-i686_2.6.1-1ubuntu5_i386.deb. But failed with "Segmentation fault" while install.

What synaptic say:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

dpkg --configure -a finished without any errors:

root@desktop:/var/cache/apt/archives# dpkg --configure -a
root@desktop:/var/cache/apt/archives#

After this apt-get still unable to to upgrade package because of segmentation fault

root@desktop:/var/cache# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pulseaudio libboost-thread1.34.0 libboost-date-time1.34.0 libc6-i686 libdb4.6 libboost-filesystem1.34.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-i686
The following packages will be upgraded:
  libc6-i686
1 upgraded, 0 newly installed, 0 to remove and 137 not upgraded.
1 not fully installed or removed.
Need to get 0B/1147kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 108934 files and directories currently installed.)
Preparing to replace libc6-i686 2.6.1-1ubuntu4 (using .../libc6-i686_2.6.1-1ubuntu5_i386.deb) ...
Segmentation fault (core dumped)

Bug created: [https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/140925](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/140925)

---

### Post by FarJumper on 2007-09-19
Any ideas?
Please help...

---

### Post by FarJumper on 2007-09-20
How can I remove this package manually? Both Autoremove and remove don't work for me:

root@desktop:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pulseaudio libboost-thread1.34.0 libboost-date-time1.34.0 libc6-i686 libdb4.6 libboost-filesystem1.34.0
The following packages will be REMOVED:
  libboost-date-time1.34.0 libboost-filesystem1.34.0 libboost-thread1.34.0 libc6-i686 libdb4.6 pulseaudio
0 upgraded, 0 newly installed, 6 to remove and 203 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 5513kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 108933 files and directories currently installed.)
Removing libc6-i686 ...
Segmentation fault (core dumped)

---

### Post by FarJumper on 2007-09-20
Problem resolved.

I manually copied /lib/tls directory from .deb package (via MC) and apt-get install -f:

root@vbuell-desktop:~# apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
root@vbuell-desktop:~# dpkg --configure -a
Setting up libc6 (2.6.1-1ubuntu5) ...
ldconfig: wrapper deferring update (trigger activated)

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@vbuell-desktop:~# dpkg --configure -a
root@vbuell-desktop:~# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 203 not upgraded.

---

### Post by FarJumper on 2007-09-20
Damn! Again. I'm panic-stricken :(

root@vbuell-desktop:~# dpkg --configure -a
root@vbuell-desktop:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg
Suggested packages:
  lzma
The following packages will be upgraded:
  dpkg
1 upgraded, 0 newly installed, 0 to remove and 240 not upgraded.
1 not fully installed or removed.
Need to get 0B/2174kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 108799 files and directories currently installed.)
Preparing to replace dpkg 1.14.5ubuntu13 (using .../dpkg_1.14.5ubuntu14_i386.deb) ...
Segmentation fault (core dumped)

---

