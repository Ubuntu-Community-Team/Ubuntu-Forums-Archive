---
title: "Kernel Version Update"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by xMoDx on 2008-11-01
Reading package lists... Done
mod@%%:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bind9-host dnsutils f-spot language-support-writing-en libavcodec1d
  libbind9-30 libisccc30 libisccfg30 linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic ssl-cert
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
mod@%%:~$ uname -r
2.6.24-16-generic
mod@%%:~$ 

i cant upgrade kernel anyone can help? :confused: thanks

i mean using safe-upgrade

---

### Post by lemming465 on 2008-11-02
Which version of Ubuntu are you running, 8.04, 8.10, ???  (cat /etc/lsb-release will say).

Does ```
sudo apt-get update; sudo apt-get upgrade --fix-broken
``` improve the situation any?

---

### Post by Cloggsy on 2008-11-05
Don't want to barge-in on someone-else's problem but I can't upgrade the kernel either and it seems the package itself which I downloaded is broken as Update Manager says 

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb: corrupted filesystem tarfile - corrupted package archive

Tried using the code you suggest above and terminal does this:

sudo apt-get update; sudo apt-get upgrade --fix-broken
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid Release.gpg
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid/restricted Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid/universe Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid/multiverse Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates Release.gpg
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates/main Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates/restricted Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates/universe Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates/multiverse Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security Release.gpg
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security/main Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security/restricted Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security/universe Translation-en_GB
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security/multiverse Translation-en_GB
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid Release    
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates Release                 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages          
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security Release
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid/main Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid/restricted Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid/universe Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid/multiverse Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates/main Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates/restricted Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates/universe Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-updates/multiverse Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security/main Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security/restricted Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security/universe Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) intrepid-security/multiverse Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.27-7-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.4MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 117836 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-7-generic 2.6.27-7.15 (using .../linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-7-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Just upgraded to Ibex

---

### Post by lemming465 on 2008-12-02
If you are still having corrupted package problems, try running **sudo apt-get clean** to remove stuff from /var/cache/apt before doing the update and upgrade.  A fresh download may do better.  (Sorry about the slow response).

---

### Post by doru001 on 2011-12-18
Should not be like this? 
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

