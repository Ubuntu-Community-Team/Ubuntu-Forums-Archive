---
title: "Installed 8.1, but  about = 8.04"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by Scott216 on 2008-11-11
I installed the new version of Ubuntu 8.1 (or so I though). But it seems I still have ver 8.04 on my IBM laptop.  If I go to the command line and run lsb_release -a, it returns:
Release: 8.04
Codename: hardy

The iso file name I used is:: ubuntu-8.10-desktop-i386.iso.  In the install process I selected 'Install Ubuntu' and for partitioning to use the entire disk.

Why do I still have 8.04?

--Scott

---

### Post by taurus on 2008-11-11
> **Scott216 said:**
> I installed the new version of Ubuntu 8.1 (or so I though). But it seems I still have ver 8.04 on my IBM laptop.  If I go to the command line and run lsb_release -a, it returns:
Release: 8.04
**[COLOR="Blue"]Codename: Handy[/COLOR]**

The iso file name I used is:: ubuntu-8.10-desktop-i386.iso.  In the install process I selected 'Install Ubuntu' and for partitioning to use the entire disk.

Why do I still have 8.04?

--Scott

Handy?

Did you have Hardy on your machine before?  What are the outputs of this command from a terminal?

```
sudo fdisk -l
df -h
```

---

### Post by Scott216 on 2008-11-11
Meant hardy, not handy.  Yes, I had 8.04 on my machine before.  I thought installing 8.10 would just overwrite and reformat everything.

Below are the results of fdisk and df commands.


Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf26cf26c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3492    28049458+  83  Linux
/dev/sda2            3493        3648     1253070    5  Extended
/dev/sda5            3493        3648     1253038+  82  Linux swap / Solaris


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              27G  2.6G   23G  11% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  424K  505M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon       27G  2.6G   23G  11% /home/scott/.gvfs

---

### Post by Scott216 on 2008-11-11
I re-downloaded the 8.10 ISO image and am reinstalling ubuntu.  The installation screens look different then before, so I think I've got the version 8.10 now.  I'm not sure how version 8.04 was named ubuntu-8.10-desktop-i386.iso, maybe one of the download mirrors had an misnamed file.

--Scott

---

