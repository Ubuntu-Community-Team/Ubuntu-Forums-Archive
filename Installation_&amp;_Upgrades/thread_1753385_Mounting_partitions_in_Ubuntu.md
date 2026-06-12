---
title: "Mounting partitions in Ubuntu"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by Replicator2011 on 2011-05-08
Hey Guys

I am new to Ubuntu but finding its a pretty cool system to use.

I set up partitions as I installed Ubuntu but cant seem to see them when I boot into Ubuntu

Is there a command or something I have to do in order to mount the hard drives.

---

### Post by towheedm on 2011-05-08
Were these partitions created during the install process or did you add them later?  If the partitions are your /home /tmp etc partitions, they are automatically mounted during boot to /home, /tmp etc.

If you created the partitions after the install use this command to mount them:
sudo mount -t fstype device directory
where fstype si the filesystem type (ext3, ext4 btrfs etc), device is the block device (/dev/sda1/ dev/sdc5 etc) and directory is the directory where you want to mount the partition to.

---

### Post by manzdagratiano on 2011-05-08
When you create partitions, UBuntu does not know which ones you wish to see by default. If you want to see a partition mounted on startup, you will have to manually edit /etc/fstab and add entries in it. Read the following guide:

[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

and you will have become a master of the fstab!!!

---

### Post by Replicator2011 on 2011-05-09
I partitioned the hard drive during the setup of Ubuntu

I know I mounted one as /
the other one i mounted as / usr i think

---

### Post by Replicator2011 on 2011-05-09
I found out some info and achieved the desired result.

Thanks for your help guys :)

---

