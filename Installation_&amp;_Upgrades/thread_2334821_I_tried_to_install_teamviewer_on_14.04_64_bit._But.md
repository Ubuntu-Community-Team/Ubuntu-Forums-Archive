---
title: "I tried to install teamviewer on 14.04 64 bit. But i couldn't install libsm6:i386."
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by wooruang on 2016-08-22
Hello,

I have Ubuntu 14.04 64bit. I have been trying to install teamviewer on my machine. But I could not install libsm6:i386 that is one of teamviewer dependencies.

I tried below.
```

sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get dist-upgrade

sudo apt-get install libsm6:i386

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libsm6:i386 : Depends: libuuid1:i386 (>= 2.16) but it is not going to be installed
E: Unable to correct problems, you have held broken packages

```

But I got the result...

So I tried to install libuuid1:i386. It required another dependencies over and over again...

Could you tell me what should I do?

---

### Post by howefield on 2016-08-23
What teamviewer version are you trying to install ?

This is how I installed teamviewer_11.0.57095_i386.deb downloaded from the Teamviewer website.

```
sudo dpkg -i /home/hugh/Downloads/teamviewer_11.0.57095_i386.deb
```

which erred with dependency issues, resolved with..

```
sudo apt-get -f --fix-missing install
```

which completed successfully and installed Teamviewer.

```
hugh@trusty:~$ sudo dpkg -i /home/hugh/Downloads/teamviewer_11.0.57095_i386.deb 
[sudo] password for hugh: 
Selecting previously unselected package teamviewer.
(Reading database ... 237253 files and directories currently installed.)
Preparing to unpack .../teamviewer_11.0.57095_i386.deb ...
Unpacking teamviewer (11.0.57095) ...
dpkg: dependency problems prevent configuration of teamviewer:
 teamviewer depends on libc6 (>= 2.4).
 teamviewer depends on libgcc1.
 teamviewer depends on libasound2.
 teamviewer depends on libdbus-1-3.
 teamviewer depends on libexpat1.
 teamviewer depends on libfontconfig1.
 teamviewer depends on libfreetype6.
 teamviewer depends on libjpeg62.
 teamviewer depends on libpng12-0.
 teamviewer depends on libsm6.
 teamviewer depends on libxdamage1.
 teamviewer depends on libxext6.
 teamviewer depends on libxfixes3.
 teamviewer depends on libxinerama1.
 teamviewer depends on libxrandr2.
 teamviewer depends on libxrender1.
 teamviewer depends on libxtst6.
 teamviewer depends on zlib1g.

dpkg: error processing package teamviewer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 teamviewer
```

```
hugh@trusty:~$ sudo apt-get -f --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libboost-system1.54.0 libcdr-0.0-0 libcmis-0.4-4 libmspub-0.0-0 libntdb1
  liborcus-0.6-0 libvisio-0.0-0 libwps-0.2-2 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic python-ntdb xfonts-mathml
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fontconfig-config gcc-4.9-base:i386 libasound2:i386 libc6:i386
  libdbus-1-3:i386 libexpat1:i386 libfontconfig1 libfontconfig1:i386
  libfreetype6:i386 libgcc1:i386 libice6:i386 libjpeg62:i386 libpng12-0:i386
  libsm6:i386 libuuid1:i386 libx11-6:i386 libxau6:i386 libxcb1:i386
  libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386
  libxinerama1:i386 libxrandr2 libxrandr2:i386 libxrender1:i386 libxtst6:i386
  zlib1g:i386
Suggested packages:
  libasound2-plugins:i386 glibc-doc:i386 locales:i386
The following NEW packages will be installed
  gcc-4.9-base:i386 libasound2:i386 libc6:i386 libdbus-1-3:i386 libexpat1:i386
  libfontconfig1:i386 libfreetype6:i386 libgcc1:i386 libice6:i386
  libjpeg62:i386 libpng12-0:i386 libsm6:i386 libuuid1:i386 libx11-6:i386
  libxau6:i386 libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386
  libxfixes3:i386 libxinerama1:i386 libxrandr2:i386 libxrender1:i386
  libxtst6:i386 zlib1g:i386
The following packages will be upgraded:
  fontconfig-config libfontconfig1 libxrandr2
3 to upgrade, 25 to newly install, 0 to remove and 85 not to upgrade.
1 not fully installed or removed.
Need to get 6,238 kB of archives.
After this operation, 16.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main gcc-4.9-base i386 4.9.3-0ubuntu4 [15.1 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libgcc1 i386 1:4.9.3-0ubuntu4 [48.0 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libc6 i386 2.19-0ubuntu6.9 [3,988 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libasound2 i386 1.0.27.2-3ubuntu7 [324 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libdbus-1-3 i386 1.6.18-0ubuntu4.3 [132 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libexpat1 i386 2.1.0-4ubuntu1.3 [71.3 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libfontconfig1 amd64 2.11.0-0ubuntu4.2 [123 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main fontconfig-config all 2.11.0-0ubuntu4.2 [47.4 kB]
Get:9 http://gb.archive.ubuntu.com/ubuntu/ trusty/main zlib1g i386 1:1.2.8.dfsg-1ubuntu1 [57.5 kB]
Get:10 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libpng12-0 i386 1.2.50-1ubuntu2.14.04.2 [119 kB]
Get:11 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libfreetype6 i386 2.5.2-1ubuntu2.5 [300 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libfontconfig1 i386 2.11.0-0ubuntu4.2 [124 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libjpeg62 i386 6b1-4ubuntu1 [75.8 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libice6 i386 2:1.0.8-2 [45.9 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libuuid1 i386 2.20.1-5.1ubuntu20.7 [11.4 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libsm6 i386 2:1.2.1-2 [17.3 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libxau6 i386 1:1.0.8-1 [8,352 B]
Get:18 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libxdmcp6 i386 1:1.1.1-1 [13.1 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libxcb1 i386 1.10-2ubuntu1 [40.6 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libx11-6 i386 2:1.6.2-1ubuntu2 [557 kB]
Get:21 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libxdamage1 i386 1:1.1.4-1ubuntu1 [7,406 B]
Get:22 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxext6 i386 2:1.3.2-1ubuntu0.0.14.04.1 [28.5 kB]
Get:23 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxfixes3 i386 1:5.0.1-1ubuntu1.1 [10.1 kB]
Get:24 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libxinerama1 i386 2:1.1.3-1 [7,900 B]
Get:25 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxrandr2 amd64 2:1.5.0-1~trusty1 [17.5 kB]
Get:26 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxrender1 i386 1:0.9.8-1build0.14.04.1 [17.5 kB]
Get:27 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main libxrandr2 i386 2:1.5.0-1~trusty1 [17.0 kB]
Get:28 http://gb.archive.ubuntu.com/ubuntu/ trusty/main libxtst6 i386 2:1.2.2-1 [13.8 kB]
Fetched 6,238 kB in 3s (2,016 kB/s)        
Preconfiguring packages ...
Selecting previously unselected package gcc-4.9-base:i386.
(Reading database ... 237542 files and directories currently installed.)
Preparing to unpack .../gcc-4.9-base_4.9.3-0ubuntu4_i386.deb ...
Unpacking gcc-4.9-base:i386 (4.9.3-0ubuntu4) ...
Selecting previously unselected package libgcc1:i386.
Preparing to unpack .../libgcc1_1%3a4.9.3-0ubuntu4_i386.deb ...
Unpacking libgcc1:i386 (1:4.9.3-0ubuntu4) ...
Selecting previously unselected package libc6:i386.
Preparing to unpack .../libc6_2.19-0ubuntu6.9_i386.deb ...
Unpacking libc6:i386 (2.19-0ubuntu6.9) ...
Replacing files in old package libc6-i386 (2.19-0ubuntu6.9) ...
Selecting previously unselected package libasound2:i386.
Preparing to unpack .../libasound2_1.0.27.2-3ubuntu7_i386.deb ...
Unpacking libasound2:i386 (1.0.27.2-3ubuntu7) ...
Selecting previously unselected package libdbus-1-3:i386.
Preparing to unpack .../libdbus-1-3_1.6.18-0ubuntu4.3_i386.deb ...
Unpacking libdbus-1-3:i386 (1.6.18-0ubuntu4.3) ...
Selecting previously unselected package libexpat1:i386.
Preparing to unpack .../libexpat1_2.1.0-4ubuntu1.3_i386.deb ...
Unpacking libexpat1:i386 (2.1.0-4ubuntu1.3) ...
Preparing to unpack .../libfontconfig1_2.11.0-0ubuntu4.2_amd64.deb ...
Unpacking libfontconfig1:amd64 (2.11.0-0ubuntu4.2) over (2.11.0-0ubuntu4.1) ...
Preparing to unpack .../fontconfig-config_2.11.0-0ubuntu4.2_all.deb ...
Unpacking fontconfig-config (2.11.0-0ubuntu4.2) over (2.11.0-0ubuntu4.1) ...
Selecting previously unselected package zlib1g:i386.
Preparing to unpack .../zlib1g_1%3a1.2.8.dfsg-1ubuntu1_i386.deb ...
Unpacking zlib1g:i386 (1:1.2.8.dfsg-1ubuntu1) ...
Selecting previously unselected package libpng12-0:i386.
Preparing to unpack .../libpng12-0_1.2.50-1ubuntu2.14.04.2_i386.deb ...
Unpacking libpng12-0:i386 (1.2.50-1ubuntu2.14.04.2) ...
Selecting previously unselected package libfreetype6:i386.
Preparing to unpack .../libfreetype6_2.5.2-1ubuntu2.5_i386.deb ...
Unpacking libfreetype6:i386 (2.5.2-1ubuntu2.5) ...
Selecting previously unselected package libfontconfig1:i386.
Preparing to unpack .../libfontconfig1_2.11.0-0ubuntu4.2_i386.deb ...
Unpacking libfontconfig1:i386 (2.11.0-0ubuntu4.2) ...
Selecting previously unselected package libjpeg62:i386.
Preparing to unpack .../libjpeg62_6b1-4ubuntu1_i386.deb ...
Unpacking libjpeg62:i386 (6b1-4ubuntu1) ...
Selecting previously unselected package libice6:i386.
Preparing to unpack .../libice6_2%3a1.0.8-2_i386.deb ...
Unpacking libice6:i386 (2:1.0.8-2) ...
Selecting previously unselected package libuuid1:i386.
Preparing to unpack .../libuuid1_2.20.1-5.1ubuntu20.7_i386.deb ...
Unpacking libuuid1:i386 (2.20.1-5.1ubuntu20.7) ...
Selecting previously unselected package libsm6:i386.
Preparing to unpack .../libsm6_2%3a1.2.1-2_i386.deb ...
Unpacking libsm6:i386 (2:1.2.1-2) ...
Selecting previously unselected package libxau6:i386.
Preparing to unpack .../libxau6_1%3a1.0.8-1_i386.deb ...
Unpacking libxau6:i386 (1:1.0.8-1) ...
Selecting previously unselected package libxdmcp6:i386.
Preparing to unpack .../libxdmcp6_1%3a1.1.1-1_i386.deb ...
Unpacking libxdmcp6:i386 (1:1.1.1-1) ...
Selecting previously unselected package libxcb1:i386.
Preparing to unpack .../libxcb1_1.10-2ubuntu1_i386.deb ...
Unpacking libxcb1:i386 (1.10-2ubuntu1) ...
Selecting previously unselected package libx11-6:i386.
Preparing to unpack .../libx11-6_2%3a1.6.2-1ubuntu2_i386.deb ...
Unpacking libx11-6:i386 (2:1.6.2-1ubuntu2) ...
Selecting previously unselected package libxdamage1:i386.
Preparing to unpack .../libxdamage1_1%3a1.1.4-1ubuntu1_i386.deb ...
Unpacking libxdamage1:i386 (1:1.1.4-1ubuntu1) ...
Selecting previously unselected package libxext6:i386.
Preparing to unpack .../libxext6_2%3a1.3.2-1ubuntu0.0.14.04.1_i386.deb ...
Unpacking libxext6:i386 (2:1.3.2-1ubuntu0.0.14.04.1) ...
Selecting previously unselected package libxfixes3:i386.
Preparing to unpack .../libxfixes3_1%3a5.0.1-1ubuntu1.1_i386.deb ...
Unpacking libxfixes3:i386 (1:5.0.1-1ubuntu1.1) ...
Selecting previously unselected package libxinerama1:i386.
Preparing to unpack .../libxinerama1_2%3a1.1.3-1_i386.deb ...
Unpacking libxinerama1:i386 (2:1.1.3-1) ...
Preparing to unpack .../libxrandr2_2%3a1.5.0-1~trusty1_amd64.deb ...
Unpacking libxrandr2:amd64 (2:1.5.0-1~trusty1) over (2:1.4.2-1) ...
Selecting previously unselected package libxrender1:i386.
Preparing to unpack .../libxrender1_1%3a0.9.8-1build0.14.04.1_i386.deb ...
Unpacking libxrender1:i386 (1:0.9.8-1build0.14.04.1) ...
Selecting previously unselected package libxrandr2:i386.
Preparing to unpack .../libxrandr2_2%3a1.5.0-1~trusty1_i386.deb ...
Unpacking libxrandr2:i386 (2:1.5.0-1~trusty1) ...
Selecting previously unselected package libxtst6:i386.
Preparing to unpack .../libxtst6_2%3a1.2.2-1_i386.deb ...
Unpacking libxtst6:i386 (2:1.2.2-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Setting up gcc-4.9-base:i386 (4.9.3-0ubuntu4) ...
Setting up fontconfig-config (2.11.0-0ubuntu4.2) ...
Setting up libfontconfig1:amd64 (2.11.0-0ubuntu4.2) ...
Setting up libxrandr2:amd64 (2:1.5.0-1~trusty1) ...
Setting up libc6:i386 (2.19-0ubuntu6.9) ...
Setting up libasound2:i386 (1.0.27.2-3ubuntu7) ...
Setting up libdbus-1-3:i386 (1.6.18-0ubuntu4.3) ...
Setting up libexpat1:i386 (2.1.0-4ubuntu1.3) ...
Setting up zlib1g:i386 (1:1.2.8.dfsg-1ubuntu1) ...
Setting up libpng12-0:i386 (1.2.50-1ubuntu2.14.04.2) ...
Setting up libfreetype6:i386 (2.5.2-1ubuntu2.5) ...
Setting up libfontconfig1:i386 (2.11.0-0ubuntu4.2) ...
Setting up libjpeg62:i386 (6b1-4ubuntu1) ...
Setting up libice6:i386 (2:1.0.8-2) ...
Setting up libuuid1:i386 (2.20.1-5.1ubuntu20.7) ...
Setting up libsm6:i386 (2:1.2.1-2) ...
Setting up libxau6:i386 (1:1.0.8-1) ...
Setting up libxdmcp6:i386 (1:1.1.1-1) ...
Setting up libxcb1:i386 (1.10-2ubuntu1) ...
Setting up libx11-6:i386 (2:1.6.2-1ubuntu2) ...
Setting up libxdamage1:i386 (1:1.1.4-1ubuntu1) ...
Setting up libxext6:i386 (2:1.3.2-1ubuntu0.0.14.04.1) ...
Setting up libxfixes3:i386 (1:5.0.1-1ubuntu1.1) ...
Setting up libxinerama1:i386 (2:1.1.3-1) ...
Setting up libxrender1:i386 (1:0.9.8-1build0.14.04.1) ...
Setting up libxrandr2:i386 (2:1.5.0-1~trusty1) ...
Setting up libxtst6:i386 (2:1.2.2-1) ...
Setting up libgcc1:i386 (1:4.9.3-0ubuntu4) ...
Setting up teamviewer (11.0.57095) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
hugh@trusty:~$
```

---

### Post by alexanderdg83 on 2016-08-23
You can also use gdebi:

```

 $ sudo apt-get update
 $ sudo apt-get install gdebi
 $ wget http://download.teamviewer.com/download/teamviewer_i386.deb
 $ sudo gdebi teamviewer_i386.deb

```

---

### Post by wooruang on 2016-08-24
Thank you. But I still have the problem.

Below I tried.
```

wooruang@wooruang-desktop:~/Downloads$ sudo dpkg -i teamviewer_11.0.57095_i386.deb 
[sudo] password for wooruang: 
Selecting previously unselected package teamviewer.
(Reading database ... 277197 files and directories currently installed.)
Preparing to unpack teamviewer_11.0.57095_i386.deb ...
Unpacking teamviewer (11.0.57095) ...
dpkg: dependency problems prevent configuration of teamviewer:
 teamviewer depends on libsm6.

dpkg: error processing package teamviewer (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 teamviewer

```
```

wooruang@wooruang-desktop:~/Downloads$ sudo apt-get -f --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  lib32z1 libexpat1:i386 libfontconfig1:i386 libice6:i386 libisl10
  libjpeg62:i386 libxinerama1:i386 linux-headers-4.2.0-27
  linux-headers-4.2.0-27-generic linux-image-4.2.0-27-generic
  linux-image-extra-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  teamviewer:i386
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 194 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 277485 files and directories currently installed.)
Removing teamviewer (11.0.57095) ...

```

Also, I tried too.

```

wooruang@wooruang-desktop:~/Downloads$ sudo apt-get update
wooruang@wooruang-desktop:~/Downloads$ sudo apt-get install gdebi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdebi is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 teamviewer:i386 : Depends: libsm6:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
```

wooruang@wooruang-desktop:~/Downloads$ sudo gdebi teamviewer_11.0.57095_i386.deb 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 
This package is uninstallable
Cannot install 'libsm6:i386'

```

I could not install libsm6:i386.

---

