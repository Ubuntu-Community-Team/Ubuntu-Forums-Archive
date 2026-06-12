---
title: "Ubuntu Server 12.04.3 LTS i386 won't install"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by joelgsf on 2013-10-06
I've been trying to install Ubuntu Server 12.04 LTS i386 from a CD-ROM on a Pentium IV 3GHz machine, always with the same problem - it doesn't manage to install linux-image-3.8.0-29-generic.
I checked the MD5 Check Sum of the ISO file and it is Ok. I checked the integrity of the CD-ROM and it is also Ok.
The error reported from syslog is transcript below (it is impossible to copy it from the console by this time):

//[FONT=System]
Errors were encountered while processing:
 /media/cdrom/pool/main/l/linux-lts-raring/linux-image-3.8.0-29-generic_3.8.0-29.42~precise1_i386.deb
Sub-process /usr/bin/dpkg returned an error code (1)
Reading pagckage lists...
Building dependency tree...
linux-headers-generic-lts-raring is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-raring: Depends: linux-image-3.8.0-29-generic but it is not going to be installed
Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)[/FONT]
//

The suggested solution of 'apt-get -f install' is inocuos, as the system can't find 'apt-get'. It also can't find dpkg.

I have previously installed Ubuntu 12.04 LTS Desktop in this same machine with no problems at all. Now I would like very much to run the Server version, as all I want to do is build a small server.
What can I do to solve this problem, please?

---

### Post by mastablasta on 2013-10-07
try to install from USB key. it could be that there is a laser lense issue

---

### Post by joelgsf on 2013-10-07
SOLVED!
It was my mistake :(. After having tried everithing else, I decided to start all over, repartitionning the disk and so on. When repartionning the disk I found that the partition "/boot" had been asigned only 1 MB, instead of 1 GB, as planned. Obviously there wasn't enough space to put the system there. Just brought it to 1 GB and, voilà! Problem solved.
Anyway, the installer could very well have detected this and signaled the lack of space! It would have been much simpler.

---

### Post by mastablasta on 2013-10-08
1 GB is huge for boot,a few MB is enough. Pentium IV 3GHz doesn't need /boot i believe (depending on your setup). if you installed 
with default it should give only / and possibly /swap (not sure with server if it actually creates this). / needs to bebig enough. i would say at least about 4 GB

---

