---
title: "apt-get Segmentation fault"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by manicman on 2006-12-14
Hello I was recently upgrading my system using the following commands
sudo apt-get update
sudo apt-get upgrade

and it hasnt configured "linux-restricted-modules-2.6.17-10-generic"
I tired to correct this using 
sudo apt-get -f install
but got the following errors
```
chris@Desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-restricted-modules-2.6.17-10-generic (2.6.17.6-1) ...
Segmentation fault
dpkg: error processing linux-restricted-modules-2.6.17-10-generic (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of nvidia-glx:
 nvidia-glx depends on nvidia-kernel-1.0.8776; however:
  Package nvidia-kernel-1.0.8776 is not installed.
  Package linux-restricted-modules-2.6.17-10-generic which provides nvidia-kernel-1.0.8776 is not configured yet.
dpkg: error processing nvidia-glx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.17-10-generic
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)
chris@Desktop:~$ 

```
I have also tried
sudo dpkg --configure -a
but i get the same problem. Im in way over my head hear and it has left me without any graphics drivers does anyone have any ideas ?

Thanks in advance
Chris

---

### Post by bapoumba on 2006-12-14
Hi,
[http://ubuntuforums.org/showthread.php?t=318206]("http://ubuntuforums.org/showthread.php?t=318206")
Does this help ?

---

