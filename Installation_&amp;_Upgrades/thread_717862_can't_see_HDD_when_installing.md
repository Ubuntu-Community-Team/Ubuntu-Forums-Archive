---
title: "can't see HDD when installing"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by ADBD on 2008-03-07
I'm running linux zenwalk now and would like to change to ubuntu. I started the installation but ubuntu didn't show my HDD (I have only one, where zenwalk is installed). It showed just some 15MB thingy, dev/fd0 I think it was. Do I need to uninstall zenwalk before installing ubuntu or why isn't the hdd showing?

edit: also the live CD is really laggy. Is it just because it's the live CD or is there some compatibility issues with my machine?

---

### Post by taurus on 2008-03-07
How much RAM do you have on your machine?  

Open a terminal and post the output of this command here regarding your harddrive.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ADBD on 2008-03-07
thanks for the quick reply,

1024 ram

from zenwalk (haven't been able to get internet connection to work on ubuntu :/):

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

---

### Post by taurus on 2008-03-07
That is a lower case letter L.

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```

---

### Post by ADBD on 2008-03-07
with fdisk -l:

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...

I guess it's different on zenwalk. I will try that on ubuntu later tonigh and post the output here.

---

### Post by taurus on 2008-03-07
In zenwalk, log in as root and run

```
fdisk -l
```

Again, that would be a lower case letter L at the end.

---

### Post by ADBD on 2008-03-07
> **taurus said:**
> In zenwalk, log in as root and run

```
fdisk -l
```

Again, that would be a lower case letter L at the end.

that's what I did. Anyways I got it working on ubuntu now, the HDD shows.

fdisk on ubuntu:
Device     Boot      Start       End              Blocks                Id        System
/dev/sda1  *          1            510              4096574+          83        Linux
/dev/sda2             511         638              1028160            82        Linus swap/Solaris
/dev/sda3             639        30401           239071297+      83        Linux

So can I just format the whole HDD on ubuntu installation and install ubuntu on it with no problems? 
I just need to get internet connection on the ubuntu live cd to work before I can give up zenwalk... In zenwalk it's just "ppoe-setup" to setup and then "pppoe-start". How do I set it up on ubuntu?

---

