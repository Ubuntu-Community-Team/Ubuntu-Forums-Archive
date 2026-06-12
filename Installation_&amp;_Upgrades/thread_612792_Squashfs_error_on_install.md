---
title: "Squashfs error on install"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by bradshoults on 2007-11-14
Ihave a Dell Poweredge 1400sc with 1 gig ram, 4 72G SCSI drives, on board video.  When I try to install I get the following error:  [290.301216] squashfs error:unable to read page, block 248A24F /sbin/init/i686/cmov/libc.so.6: cannot read file data: i/o error.
I am able to install Mandriva, Fedora, Suse, and even Knoppix on this pc, but Ubuntu will no install?
I am not going to settle for that as I am pretty sure that Ubuntu is the best distro and I will get it on this pc- with alot of help I am sure.  So if you can help me I will be most greatful.

---

### Post by ds6 on 2007-11-14
I have a Dell PowerApp BigIP server with SCSI hardware that is giving the exact same errors. I have tried the Ubuntu 7.04 server and DT, 7.10 server and desktop, Fedora 8 LiveCD. No luck on any of those. I'm sure it has something to do with the SCSI drives.

How can I change the drive that the OS is loading to? 

Thx

---

### Post by bradshoults on 2007-11-17
from what I can tell the os is not loading onto any disk, it boots off of the live cd first and then you have the option to install. once it gets to the error the scsi subsystem has already been loaded. I just can't find out how to get past the squashfs error.

---

