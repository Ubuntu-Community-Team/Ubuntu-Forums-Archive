---
title: "Cannot install xorg-dev package!!"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by johnkgoahead on 2010-03-05
tbis is the system of ubuntu 8.04

i run "sudo apt-get install xorg-dev" and the following is shown.

johnk@johnk-laptop:~$ sudo apt-get install xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-23-generic linux-headers-2.6.24-23
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev libexpat1-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev libxfont-dev libxft-dev linux-libc-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev libexpat1-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev libxfont-dev libxft-dev linux-libc-dev xorg-dev zlib1g-dev
0 upgraded, 10 newly installed, 0 to remove and 9 not upgraded.
Need to get 4050kB/5933kB of archives.
After this operation, 24.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-24.59
  404 Not Found [IP: 91.189.88.40 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4
  404 Not Found [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-libc-dev 2.6.24-24.59
  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-24.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-24.59_i386.deb)  404 Not Found [IP: 91.189.88.37 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.7-10ubuntu4_i386.deb](http://hk.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.7-10ubuntu4_i386.deb)  404 Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


then i try its bug report with --fixing-missing...

johnk@johnk-laptop:~$ sudo apt-get install xorg-dev --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-23-generic linux-headers-2.6.24-23
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev libexpat1-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev libxfont-dev libxft-dev linux-libc-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev libexpat1-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev libxfont-dev libxft-dev linux-libc-dev xorg-dev zlib1g-dev
0 upgraded, 10 newly installed, 0 to remove and 9 not upgraded.
Need to get 4050kB/5933kB of archives.
After this operation, 24.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-24.59
  404 Not Found [IP: 91.189.88.45 80]
Err [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4
  404 Not Found [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main linux-libc-dev 2.6.24-24.59
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-24.59_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.24-24.59_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.7-10ubuntu4_i386.deb](http://hk.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.7-10ubuntu4_i386.deb)  404 Not Found [IP: 91.189.88.45 80]


i tried to find the updates and they really dont exist...
how can i install the package?

---

### Post by iponeverything on 2010-03-05
run:

```
sudo apt-get update
```

before sudo apt-get install xorg-dev

---

### Post by johnkgoahead on 2010-03-05
It works!!! Thank you a lot!!!

---

