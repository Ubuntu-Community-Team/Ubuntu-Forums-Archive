---
title: "initramfs-tools broken"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by marios88 on 2006-11-23
please help i searched the forums but nothing solved my problem...


```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools
The following NEW packages will be installed:
  initramfs-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/50.1kB of archives.
After unpacking 356kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 9980 files and directories currently installed.)
Unpacking initramfs-tools (from .../initramfs-tools_0.69ubuntu20_all.deb) ...
sed: no input files
dpkg: error processing /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 4
Errors were encountered while processing:
 /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by marios88 on 2006-11-27
I solved the problem just downgrade to ver 0.40 from the ftp 

[http://ftp.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/](http://ftp.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/)

---

