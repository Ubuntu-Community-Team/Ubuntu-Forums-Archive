---
title: "Ubuntu 8.10 on usb-stick (unetbootin install) apt-get problem"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by p.becks on 2008-11-04
Hello,

Whenever i apt-get something i always get this error at the end:

**********************************************************

Setting up linux-image-2.6.27-7-generic (2.6.27-7.15) ...
Running depmod.
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.27-7-generic to initrd.img.
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-7-generic; however:
  Package linux-image-2.6.27-7-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.7.11); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.27-7-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error 



What's wrong?

---

### Post by Partyboi2 on 2008-11-04
what happens when you open a terminal (Applications>Accessoires>Terminal) and
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by p.becks on 2008-11-04
ubuntu@ubuntu:~$ sudo dpkg --configure -a 
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-7-generic; however:
  Package linux-image-2.6.27-7-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.7.11); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic
 linux-generic
ubuntu@ubuntu:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27-7-generic (2.6.27-7.15) ...
Running depmod.
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.27-7-generic to initrd.img.
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-7-generic; however:
  Package linux-image-2.6.27-7-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.7.11); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.27-7-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$

---

