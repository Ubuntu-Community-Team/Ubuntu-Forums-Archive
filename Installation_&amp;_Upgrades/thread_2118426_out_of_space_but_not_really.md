---
title: "out of space but not really"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2013-02-21
I was out of disk space but I fixed that.
I have a broken package that I can't fix because it thinks it's still out of disk space.

root@other:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-38
The following NEW packages will be installed:
  linux-headers-3.2.0-38
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 11.7 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/main linux-headers-3.2.0-38 all 3.2.0-38.60 [11.7 MB]
Fetched 11.7 MB in 23s (503 kB/s)                                              
(Reading database ... 448297 files and directories currently installed.)
Unpacking linux-headers-3.2.0-38 (from .../linux-headers-3.2.0-38_3.2.0-38.60_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-38_3.2.0-38.60_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-38/include/net/netns/mib.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-38/include/net/netns/mib.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-38_3.2.0-38.60_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@other:~# df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1        7372864 5490320   1508016  79% /

---

### Post by albandy on 2013-02-21
Is this a virtual machine?

---

### Post by kc1di on 2013-02-21
Try this one 

```
sudo dpkg --configure -a
```
see if that works for you.

---

### Post by bjlockie on 2013-02-21
> **albandy said:**
> Is this a virtual machine?


Nope, real netbook.

---

### Post by bjlockie on 2013-02-21
> **kc1di said:**
> Try this one 

```
sudo dpkg --configure -a
```
see if that works for you.

# dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-headers-3.2.0-38-generic:
 linux-headers-3.2.0-38-generic depends on linux-headers-3.2.0-38; however:
  Package linux-headers-3.2.0-38 is not installed.
dpkg: error processing linux-headers-3.2.0-38-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-3.2.0-38-generic

---

### Post by fuorviatos on 2013-02-21
You can try as well (This will delete all the updates on your hard drive you've installed or you were planning to install)

> cd /var/lib/dpkg/updates
rm *

---

### Post by bjlockie on 2013-02-21
I tried dpkg --configure -a --force-all

# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-headers-3.2.0-38
The following NEW packages will be installed:
  linux-headers-3.2.0-38
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/11.7 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 448297 files and directories currently installed.)
Unpacking linux-headers-3.2.0-38 (from .../linux-headers-3.2.0-38_3.2.0-38.60_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-38_3.2.0-38.60_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-38/arch/ia64/include/asm/sn/pcibus_provider_defs.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-38/arch/ia64/include/asm/sn/pcibus_provider_defs.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-38_3.2.0-38.60_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bjlockie on 2013-02-21
Could it be my SSD is failing?

---

### Post by fuorviatos on 2013-02-21
> **bjlockie said:**
> Could it be my SSD is failing?
Still hard to say. If you SSD is recent it should have the SMART feature. There are plenty of tools in Ubuntu to check hard drive health. 
Have a look here for further info [http://ubuntuforums.org/showthread.php?t=881617](http://ubuntuforums.org/showthread.php?t=881617)

---

### Post by kc1di on 2013-02-21
if you find the H.D. is ok give these a try:

```
sudo apt-get autoclean
sudo apt-get clean

```
if that does not work do the following and try the install again.

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by bjlockie on 2013-02-22
Nothing worked.

fsck didn't find a problem.

I did
dpkg -r linux-headers*
and it seems to work now.

---

### Post by kc1di on 2013-02-22
Glad you found a soulution :)

---

