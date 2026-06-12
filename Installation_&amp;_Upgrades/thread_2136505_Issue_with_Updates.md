---
title: "Issue with Updates"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by LinuxNoob6 on 2013-04-17
All,

When I try to run update manager on Ubuntu 12.04.2 LTS, I'm getting the error:

```
installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/available' near line 17840 package 'x11-utils': newline in field name `Maintaine2b6f877c886859d7d65518292b'
Error in function: 
```

If I run ```
sudo apt-get clean all
``` from the terminal, I get:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libcurl3-gnutls libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2
  libsmbclient libwbclient0 samba-common samba-common-bin xserver-common
  xserver-xorg-core
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.7 MB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm2 i386 2.4.39-0ubuntu0.2 [27.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-intel1 i386 2.4.39-0ubuntu0.2 [63.3 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-nouveau1a i386 2.4.39-0ubuntu0.2 [14.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-radeon1 i386 2.4.39-0ubuntu0.2 [23.1 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcurl3-gnutls i386 7.22.0-3ubuntu4.1 [233 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libwbclient0 i386 2:3.6.3-2ubuntu2.6 [31.0 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libsmbclient i386 2:3.6.3-2ubuntu2.6 [2,135 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main samba-common all 2:3.6.3-2ubuntu2.6 [326 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main samba-common-bin i386 2:3.6.3-2ubuntu2.6 [6,150 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-common all 2:1.11.4-0ubuntu10.13 [31.5 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-core i386 2:1.11.4-0ubuntu10.13 [1,676 kB]
Fetched 10.7 MB in 8s (1,205 kB/s)                                             
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/available' near line 17840 package 'x11-utils':
 newline in field name `Maintaine2b6f877c886859d7d65518292b'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I've searched the forums but can't see to find anything with this exact error.

Please help!

TIA,

LinuxNoob

---

### Post by plucky on 2013-04-18
What does ```
sudo dpkg --clear-avail
sudo apt-get update
``` do for you?

Good Luck

---

### Post by LinuxNoob6 on 2013-04-18
That fixed it!

Thanks!!!!

---

