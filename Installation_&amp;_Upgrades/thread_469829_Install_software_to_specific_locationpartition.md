---
title: "Install software to specific location/partition"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by chalewa on 2007-06-10
ok so i have this script to install a piece of software, i want to install it to a partition different than my root partition...specifically i want to install it to /media/sda2 


any help would be appreciated

---

### Post by taurus on 2007-06-10
What does the script to install that software look like and what filesystem is /dev/sda2?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by chalewa on 2007-06-10
> **taurus said:**
> What does the script to install that software look like and what filesystem is /dev/sda2?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```



fdisk returns 

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825       28073   210845092+  83  Linux
/dev/sda3           28074       30395    18643401   82  Linux swap / Solaris

```

cat /etc/fstab returns 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=53a475f8-7483-4e28-997e-d291be54f7e4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=b5436eab-db73-4213-a4db-0d1f9aad917d /media/sda2     ext3    defaults        0       2
# /dev/sda3
UUID=502a9097-a326-4ac0-bc85-679597c60e54 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2007-06-10
Are you, username, the owner of /media/sda2 or does root own it?  If you want to write to it, /media/sda2, you need to be the owner of that directory.  What program do you plan to install to /media/sda2 anyway?

Basically, you can create something like /media/sda2/bin and install all your extra apps in there.  Then, add /media/sda2/bin to your path in ~/.bashrc so you can run all the programs in there without typing in the whole path.

```
ls -la /media
```

---

### Post by chalewa on 2007-06-10
> **taurus said:**
> Are you, username, the owner of /media/sda2 or does root own it?  If you want to write to it, /media/sda2, you need to be the owner of that directory.  What program do you plan to install to /media/sda2 anyway?

Basically, you can create something like /media/sda2/bin and install all your extra apps in there.  Then, add /media/sda2/bin to your path in ~/.bashrc so you can run all the programs in there without typing in the whole path.

```
ls -la /media
```

yea i own it...

i just want to install hellanzb there because the only thing that i have installed on my root partition is the OS, and I use the other partition for storage

---

