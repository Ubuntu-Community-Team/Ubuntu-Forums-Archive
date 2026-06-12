---
title: "Ubuntu 15.04 server segfault"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by zkab on 2015-04-23
Hi,

I just installed Ubuntu 15.04 server (AMD64) daily built today.
After first reboot dmesg gave me this (before I even started to install my software):

[   12.830672] ifquery[434]: segfault at 1 ip 00000000004031c8 sp 00007ffe7ea53c60 error 4 in ifup[400000+d000]

The server has two disks and I used the option 'Use entire disk' for the first disk - the second sata disk is not partioned yet ...
What is wrong ?

---

### Post by dino99 on 2015-04-23
there is still some known issues  [https://wiki.ubuntu.com/VividVervet/ReleaseNotes](https://wiki.ubuntu.com/VividVervet/ReleaseNotes)
but maybe check the md5sum  or redownload [http://cdimage.ubuntu.com/ubuntu-server/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/daily/current/)

---

### Post by zkab on 2015-04-23
I checked with SHA1SUMS  before installation and it was OK.
Can't reload and reinstall since I have already continued with my software installation ...
I hope the issues will be solved with new updates ...

---

