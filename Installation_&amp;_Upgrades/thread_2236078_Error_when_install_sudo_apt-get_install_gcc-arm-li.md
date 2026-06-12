---
title: "Error when install sudo apt-get install gcc-arm-linux-gnueabi"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by Loufa on 2014-07-24
hello, 

I'm trying to install gcc-arm-linux-gnueabi but it gives me the following errors:
.
.
.
```
Setting up grub-pc (2.02~beta2-9ubuntu1) ...
awk: fatal: can't stat fd 0 (Invalid argument)
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
after some search here what i tried:

```
sudo dpkg --configure -a
Setting up grub-pc (2.02~beta2-9ubuntu1) ...
awk: fatal: can't stat fd 0 (Invalid argument)
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 grub-pc

sudo apt-get purge grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.11.0-18-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.11.0-18-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 614 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 319842 files and directories currently installed.)
Removing grub-gfxpayload-lists (0.6) ...
Removing grub-pc (2.02~beta2-9ubuntu1) ...
Purging configuration files for grub-pc (2.02~beta2-9ubuntu1) ...
awk: fatal: can't stat fd 0 (Invalid argument)
dpkg: error processing package grub-pc (--purge):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get install grub-pc --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.11.0-18-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.11.0-18-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-gfxpayload-lists
The following NEW packages will be installed:
  grub-gfxpayload-lists grub-pc
0 upgraded, 2 newly installed, 0 to remove and 11 not upgraded.
Need to get 0 B/176 kB of archives.
After this operation, 614 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
Selecting previously unselected package grub-pc.
(Reading database ... 319821 files and directories currently installed.)
Preparing to unpack .../grub-pc_2.02~beta2-9ubuntu1_amd64.deb ...
Unpacking grub-pc (2.02~beta2-9ubuntu1) ...
Selecting previously unselected package grub-gfxpayload-lists.
Preparing to unpack .../grub-gfxpayload-lists_0.6_amd64.deb ...
Unpacking grub-gfxpayload-lists (0.6) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up grub-gfxpayload-lists (0.6) ...
Setting up grub-pc (2.02~beta2-9ubuntu1) ...
awk: fatal: can't stat fd 0 (Invalid argument)
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.11.0-18-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.11.0-18-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-pc (2.02~beta2-9ubuntu1) ...
awk: fatal: can't stat fd 0 (Invalid argument)
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

can someone help me

Thanks

---

### Post by slickymaster on 2014-07-24
Hey Loufa, I've edit your post [adding code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to it. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand and the use of 'Code' tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Loufa on 2014-07-24
Thanks

---

### Post by Loufa on 2014-07-24
Thanks, every thing went fine now i just reinstalled grup from the software center. :)

---

### Post by slickymaster on 2014-07-24
Glad you got it fixed.

Please don't forget to mark the thread as SOLVED. Here's [how you do it]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Loufa on 2014-07-24
Hello,

the error repeated again when try to build kernel:
```

./build_kernel.sh
+ Detected build host [Ubuntu 14.04 LTS]
+ host: [x86_64]
+ git HEAD commit: [fdfdbd0d391eecb9645ea18af1bf380c7ad54046]
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
awk: fatal: can't stat fd 0 (Invalid argument)
Debian/Ubuntu/Mint: missing dependencies, please install:
-----------------------------
sudo apt-get update
sudo apt-get install bc build-essential device-tree-compiler fakeroot lsb-release lzma lzop man-db u-boot-tools libncurses5-dev:amd64 libc6:i386 libncurses5:i386 libstdc++6:i386 zlib1g:i386 
-----------------------------
* Failed dependency check


```

i tried the two command but no luck

---

