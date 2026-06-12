---
title: "Partitioning question and others"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by satimis on 2007-07-24
Hi folks,

CPU - AMD Athlon64 X2 3800
RAM - 2G 6400 dual channel
HD - 160G
Ubuntu 7.04 server amd64 (LAMP) 
virtualbox


I'm building a Virtual Machine with Ubuntu as host OS.  I shall run Slackware-i386 and OpenBSD4.1-amd64 as guess OS

Following Guide Partition finally it came to;```

LVM   VG  Ubuntu  LV root - 153.5  Linux device-mapper
          #1   153.5 GB   f  ext3   /
LVM   VG  Ubuntu  LV swap_1  6.3G  Linux device-mapper
          #1    6.3GB     f   swap   swap
SCSI2   (0,0,0)  (sda)  -  160.0GB  ATA  maxtor  6V160E0
          #1   Primary   255.0 MB   B   F   ext3   /boot
          #5   Logical    159.8 GB   k   lvm

```

Please help me to understand:-
1) What is #1?  Is it partition-1?

2) What is #5?  Is it partition-5?  Then where are partition-2/3/4?

3) Why it needs 6.3GB as swap.  RAM size is only 2G.


In order to reserve space on the HD for the guest OSs, I deleted;```

#1   153.5 GB   f  ext3   /

```
and recreated it```

#1   40GB   f  ext3  /

```
leaving 113.5GB space unusable.  Can I use this space for installing the guest OS, Slackware-i386 and OpenBSD4.1-amd64?


Now Ubuntu 7.04 server (LAMP) is running but without X and DNS installed.


I'm prepared to install virtualbox as virtualizer but can't find it with;
$ sudo apt-cache show/showpkg vituralbox

Nor vmware-server.  I found qemu and bochs.  Which repo I have to enable?

Please advise.   TIA


B.R.
satimis

---

