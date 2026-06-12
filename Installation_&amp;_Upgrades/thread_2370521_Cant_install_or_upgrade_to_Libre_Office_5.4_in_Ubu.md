---
title: "Cant install or upgrade to Libre Office 5.4 in Ubuntu 16.04 LTS"
date: 2017-09-04
forum: Installation &amp; Upgrades
---

### Post by Semn on 2017-09-04
Trying to upgrade or download a fresh installation of Libre Office, I get:
```
sem@sem-Latitude-E6430:~/Desktop/LibreOffice_5.4.1.2_Linux_x86-64_deb/DEBS$ sudo apt-get install ppa-purge && sudo ppa-purge ppa:libreoffice/ppa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libllvm3.8 libllvm3.8:i386 linux-headers-4.4.0-81
  linux-headers-4.4.0-81-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-headers-4.4.0-89
  linux-headers-4.4.0-89-generic linux-image-4.4.0-81-generic
  linux-image-4.4.0-83-generic linux-image-4.4.0-87-generic
  linux-image-4.4.0-89-generic linux-image-extra-4.4.0-81-generic
  linux-image-extra-4.4.0-83-generic linux-image-extra-4.4.0-87-generic
  linux-image-extra-4.4.0-89-generic
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  aptitude
The following NEW packages will be installed:
  ppa-purge
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
Need to get 6 312 B of archives.
After this operation, 24,6 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 ppa-purge all 0.2.8+bzr63 [6 312 B]
Fetched 6 312 B in 0s (68,8 kB/s)       
Selecting previously unselected package ppa-purge.
(Reading database ... 564195 files and directories currently installed.)
Preparing to unpack .../ppa-purge_0.2.8+bzr63_all.deb ...
Unpacking ppa-purge (0.2.8+bzr63) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up ppa-purge (0.2.8+bzr63) ...
Updating packages lists
W: The repository 'http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu xenial Release' does not have a Release file.
W: The repository 'http://ppa.launchpad.net/strukturag/libde265/ubuntu xenial Release' does not have a Release file.
E: Failed to fetch [http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Failed to fetch [http://ppa.launchpad.net/strukturag/libde265/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/strukturag/libde265/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
sem@sem-Latitude-E6430:~/Desktop/LibreOffice_5.4.1.2_Linux_x86-64_deb/DEBS$ 
```

Then, when opening the existing Libre Office, its 5.1, no matter what I try.

---

### Post by ajgreeny on 2017-09-04
You are trying to use the wrong ppa, and I am a bit lost with the commands you used which do not make total sense to me, so remove the ppa you appear to have added, 
**[http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu) xenial Release** 
which does not exist, and try 
```
sudo add-apt-repository ppa:libreoffice/ppa
``` 
which will give you version: 5.4.1.2 which works fine.  I've been using that ppa for a long time and never had problems for any of my simple needs of an office suite.

If any ppa purge command is not working, you can simply look for the libreoffice ppa file in** /etc/apt/sources.list.d/** and remove it from there, then add the one I suggest.

---

