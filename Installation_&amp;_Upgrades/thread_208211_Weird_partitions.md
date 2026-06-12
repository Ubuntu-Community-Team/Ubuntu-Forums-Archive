---
title: "Weird partitions?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by urbandryad on 2006-07-03
I'm starting to wonder if my system isn't set up right. I'm using Xubuntu, but only have 1.4 GIGs free? Less than what I'd have with the same settings for Ubuntu? That doesn't seem right. :( What are all these partitions for? Are they are part of dapper?


/dev/hda3             2.9G  1.4G  1.4G  49% /
varrun                 46M   88K   46M   1% /var/run
varlock                46M  4.0K   46M   1% /var/lock
udev                   46M  108K   46M   1% /dev
devshm                 46M     0   46M   0% /dev/shm
lrm                    46M  480K   46M   2% /lib/modules/2.6.15-25-powerpc/volatile

---

### Post by aysiu on 2006-07-04
/dev/hda3 is the only partition in the list. I don't know what those other things are.

For example, this is what mine looks like: ```
df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/hda7             8.8G  3.3G  5.1G  40% /**
varrun                221M   92K  221M   1% /var/run
varlock               221M  4.0K  221M   1% /var/lock
udev                  221M  140K  221M   1% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   19M  202M   9% /lib/modules/2.6.15-25-386/volatile
**/dev/hda5             123G   48G   70G  41% /documents**
``` I have only two partitions mounted.

---

### Post by john_markh on 2006-07-04
Can you post :
df -h
fdisk -l

---

### Post by aysiu on 2006-07-04
[QUOTE=john_markh]Can you post :
df -h
fdisk -l[/QUOTE]
That is *df -h* in the first post.

---

### Post by houstonbofh on 2006-07-04
You df -h gave you the file system.  Now fdisk will give you the drive.
> admin@ubuntu-desktop:~$ sudo fdisk /dev/hda -l
Password:****

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris
admin@ubuntu-desktop:~$


---

