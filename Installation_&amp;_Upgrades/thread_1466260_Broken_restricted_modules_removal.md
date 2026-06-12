---
title: "Broken restricted modules removal"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by anomit on 2010-04-30
Last week I upgraded the kernel from 2.6.28 to 2.6.31. I mistakenly removed the 2.6.28 directory from lib/modules without first actually removing them through apt-get. I completely forgot about this and recently tried removing the linux-image package for 2.6.28 through synaptic which also included the restricted drivers package. Since obviously the directory doesn't exist now, it failed. Now everytime I try any apt-get operation, like installing another package, it first tries to remove that restricted drivers package, fails and aborts without installing the packages I requested[1]. Please help me out of this sticky situation.

[1]An example listing:

```
$ sudo apt-get install mit-scheme
[sudo] password for anomit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmcrypt4 libmhash2
Suggested packages:
  libmcrypt-dev mcrypt mit-scheme-dbg
The following packages will be REMOVED:
  linux-restricted-modules-2.6.28-18-generic
The following NEW packages will be installed:
  libmcrypt4 libmhash2 mit-scheme
0 upgraded, 3 newly installed, 1 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 7,023kB of archives.
After this operation, 16.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com karmic/universe libmcrypt4 2.5.8-3 [85.7kB]
Get:2 http://archive.ubuntu.com karmic/main libmhash2 0.9.9-1build1 [114kB]
Get:3 http://archive.ubuntu.com karmic/universe mit-scheme 7.7.90+20090107-1ubuntu1 [6,823kB]
Fetched 7,023kB in 2min 1s (57.7kB/s)                                                                                         
(Reading database ... 189334 files and directories currently installed.)
Removing linux-restricted-modules-2.6.28-18-generic ...
rmdir: failed to remove `/lib/modules/2.6.28-18-generic/volatile/': No such file or directory
WARNING: Couldn't open directory /lib/modules/2.6.28-18-generic: No such file or directory
FATAL: Could not open /lib/modules/2.6.28-18-generic/modules.dep.temp for writing: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.28-18-generic
Cannot find /lib/modules/2.6.28-18-generic
update-initramfs: failed for /boot/initrd.img-2.6.28-18-generic
dpkg: error processing linux-restricted-modules-2.6.28-18-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-18-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ankle on 2010-05-03
Try making an empty directory in /lib/modules:
```
sudo mkdir /lib/modules/2.6.28-18-generic
```

---

### Post by xiaohwan on 2010-05-10
I got the same trouble. To solve it just copy another folder like 2.6.32-22-generic to /lib/modules and rename it to what you need, then try remove the package by apt-get.

paul

---

