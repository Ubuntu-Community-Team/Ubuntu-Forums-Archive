---
title: "Synaptic broken cache"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by SirPecanGum on 2006-09-21
Firstly, according to Synaptic I have a total of 2 packages installed (belocs-locales-bin and locales). If I try to install anything or update the system or fix the 1 broken package listed (libc6_2.3.6-0ubuntu20_i386.deb) I get this response from Synaptic: E: /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb: subprocess pre-installation script returned error exit status 1

I haven't seen any other similar errors reported on this forum but I have tried a few other things, for example:

$ sudo apt-get install -f

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following NEW packages will be installed
  libc6
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/4588kB of archives.
After unpacking 10.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Cannot get debconf version. Is debconf installed?
debconf: apt-extracttemplates failed: Bad file descriptor(Reading database ... 2318 files and directories currently installed.)
Unpacking libc6 (from .../libc6_2.3.6-0ubuntu20_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !
dpkg: error processing /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.3.6-0ubuntu20_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

$

System is still up and running and reboots, I'm using it now. Things turned sour after I installed PCLOS on another partition and had to make a bastard menu.lst file - worked though! Well, perhaps not quite if this is the result.

Looks to me like another full reinstall - tinkered to death as my brother keeps saying...again! 

I thank you if you can help. In any event, I haven't had so much fun since the Rubik's cube! Thank you very much indeed!

---

### Post by SirPecanGum on 2006-09-22
I have also tried sudo 

apt-get -f remove

apt-get upgrade -f dist-upgrade

dpkg --configure -a

dpkg -r package

dpkg --purge package libc6_2.3.6-0ubuntu20_i386.deb

dpkg --force-auto-select libc6_2.3.6-0ubuntu20_i386.deb

All responding with much the same excuse as above.

I have been Ubunting for only a few weeks and so far, I am reinstalling Linux as often as I reboot Windows :rolleyes:  Surely that isn't right?! To be fair I should mention that I am digging deep while I tinker and explore and to remove stuff like Bluetooth and Printer related services which, since I don't have I don't want installed.

---

