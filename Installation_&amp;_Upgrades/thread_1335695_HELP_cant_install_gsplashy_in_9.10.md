---
title: "HELP cant install gsplashy in 9.10??"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by xenosaga456 on 2009-11-23
ya can someone help me properly install splashy....i found this web site
 [http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25]("http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25") and i follow all of there directions but when i try install splashy_0.3.10-1_i386.deb the deb manager gives me this

```
 Error: Dependency is not satisfiable: libdirectfb-1.0-0 (>= 1.0.1-9)
```


so then i try to install libsplashy1_0.3.10-1_i386.deb first and deb manager gives me this 

```
Error: A later version is already installed
```



so the i try to go to Synaptic Package Manage and i Search: splashy
i found it and marked it for install and it spits out this 


```
E: /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb: trying to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 0
```

so i try terminal ( sudo apt-get install splashy )

```
me@this-laptop:~$ sudo apt-get install splashy
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  splashy-themes console-common
The following packages will be REMOVED:
  usplash usplash-theme-ubuntu
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/1,181kB of archives.
After this operation, 1,417kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 153728 files and directories currently installed.)
Removing usplash-theme-ubuntu ...
update-initramfs: deferring update (trigger activated)
Removing usplash ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Processing triggers for man-db ...
Processing triggers for sreadahead ...
(Reading database ... 153708 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-5ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb (--unpack):
 trying to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 0:4.0-0ubuntu5
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


PLEASE HELP Me im using ubuntu 9.10 kernal 2.6.31-14-generic 32bit

---

### Post by steve19137 on 2010-01-06
yes. i am having the same issues!!! i want it for the mac4lin theme. please help!!!!

---

### Post by jeffymarts on 2010-01-07
Same problem here. I am also running the same version, and getting the same exact problem.

---

