---
title: "Help Burning an ISO"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by cac007 on 2006-07-24
This is what happens when i run gnomebaker:

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdb'
devname: '/dev/hdb'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdb exclusively (Device or resource busy)... retrying in 1 second.
cdrecord: Device or resource busy. Cannot open '/dev/hdb'. Cannot open SCSI driver.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

This is me running scanbus

cory@ubuntu:~/Desktop$ sudo cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

Any Help?

---

### Post by frodon on 2006-07-24
Duplicate thread.

Please answer in this thread : [http://ubuntuforums.org/showthread.php?t=221905](http://ubuntuforums.org/showthread.php?t=221905)

Closed

---

