---
title: "Unable to install anything.."
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by BalaViknesh on 2010-08-04
Guys,

am unable to installl anything.. it says installer crashed and wants me to send report to ubuntu..

bala@Bala:~$ sudo apt-get install pppoe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  usb-modeswitch-data usb-modeswitch
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  pppoe
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 96.5kB of archives.
After this operation, 319kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe pppoe 3.8-3 [96.5kB]
Fetched 96.5kB in 1min 4s (1,506B/s)                                           
Selecting previously deselected package pppoe.
(Reading database ... 190941 files and directories currently installed.)
Unpacking pppoe (from .../archives/pppoe_3.8-3_i386.deb) ...
Processing triggers for man-db ...
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-999-generic
Building for architecture i686
Building initial module for 2.6.35-999-generic

Error! Bad return status for module build on kernel: 2.6.35-999-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up pppoe (3.8-3) ...
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
bala@Bala:~$ sudo apt-get install pppoe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pppoe is already the newest version.
The following packages were automatically installed and are no longer required:
  usb-modeswitch-data usb-modeswitch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-999-generic
Building for architecture i686
Building initial module for 2.6.35-999-generic

Error! Bad return status for module build on kernel: 2.6.35-999-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
**E: Sub-process /usr/bin/dpkg returned an error code (1)**
bala@Bala:~$ 


I have pasted above the error which i got while installing pppoe... 

can you please resolve this...

---

### Post by BalaViknesh on 2010-08-06
After changing 2.6.32 it worked'

---

### Post by tommcd on 2010-08-06
> **BalaViknesh said:**
> After changing 2.6.32 it worked'
Sometimes, this is the price you pay for an education. In Ubuntu, stick with the kernel that is provided if you can. The Ubuntu kernels are heavily patched. If you compile your own kernel, you will loose some functionality that the default kernel provided.

Note: Already compiled Ubuntu kernels can be downloaded from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by BalaViknesh on 2010-08-08
Thanx Tomm...  Worthy Lesson Learnt... :)

---

