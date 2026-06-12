---
title: "Alert! dev/disk .... does not exist problem"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by questionblaine on 2007-05-05
I did the upgrade from edgy to fawn using update manager.  When I restart, the system sits there for about 5 minutes then displays:

Alert! dev/disk/by -uuid/09d8d406-6c24-4438-bf27-4a17oe4e718 does not exist.

What do I do now???

Blaine

---

### Post by taurus on 2007-05-05
Can you boot your machine with the LiveCD?  Then, post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by questionblaine on 2007-05-05
first of all, THANK YOU for helping me.

This is what I get:
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4910    39439543+   7  HPFS/NTFS
/dev/hda2            4911        9529    37102117+  83  Linux
/dev/hda3            9530        9729     1606500    5  Extended
/dev/hda5            9530        9729     1606468+  82  Linux swap / Solaris

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9976    80132188+  83  Linux
/dev/hdb2           19578       19929     2827440    5  Extended
/dev/hdb3   *        9977       19577    77120032+  83  Linux
/dev/hdb5           19849       19929      650601   82  Linux swap / Solaris
/dev/hdb6           19578       19848     2176744+  82  Linux swap / Solaris

Partition table entries are not in disk order


I am running Kubuntu on hda2

Blaine

---

### Post by taurus on 2007-05-05
Okay, open a terminal and mount your Kubuntu, /dev/hda2, so we can have a look at your /etc/fstab.

```
sudo mkdir /media/kubuntu
sudo mount -t ext3 /dev/hda2 /media/kubuntu
cat /media/kubuntu/etc/fstab
```
(Post the output of the last command here.)

---

### Post by questionblaine on 2007-05-05
Sorry it took so long to get back. someone else is using this computer as well

Here is what I got

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdnumber2 ext2  defaults         0         0

---

### Post by skrat on 2007-06-13
I have same problem with freshly installed Feisty on similar configuration:

hda1  NTFS/Windows
hda2  / reiserfs
hda3 /home/ reiserfs
hda4 swap

Edit: Installation was from original Ubuntu CD

---

### Post by skrat on 2007-06-13
The following procedure solved the problem for me:

1. Boot LiveCD
2. create /media/newroot/ and mount / on HD  to it (in my case/dev/hda2) 
```

mkdir /media/newroot/
mount /dev/hda2 /media/newroot/ 

```
3. chroot to /media/newroot/
```

chroot /media/newroot/

```
3. update and dist-upgrade
```

apt-get update
apt-get dist-upgrade

```
This installs new kernel 2.6.20-16 and after that system boots normally.

---

