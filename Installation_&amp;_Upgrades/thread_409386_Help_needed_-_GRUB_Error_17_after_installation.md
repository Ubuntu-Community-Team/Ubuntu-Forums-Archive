---
title: "Help needed - GRUB Error 17 after installation"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by AsaCeva on 2007-04-14
Hi All,
I need some urgent help.
I have just installed Ubuntu 6.10 (using irqpoll option, otherwise it doesn't work) without any errors, but after installation it gives me GRUB Error 17. 
(I am currently using the live Ubuntu CD to find some help).

I have the following system
Intel PIV 
40 GB IDE hard drive running WIndows XP
40 GB IDE hard drive where I installed Ubuntu
250 GB SATA hard drive partitioned in 3 parts, 2 of them formatted as NTFS.

My intention was to leave WinXP on the first HD, and install Ubuntu on the second IDE HD. 
Currently, I can use only the live CD, so any help will be much appreciated.
Thanks folks.

Below is some information that my help:

/dev has the following hard drives:
ubuntu@ubuntu:~$ ll /dev/hda
brw-rw---- 1 root disk 3, 0 2007-04-14 13:08 /dev/hda
ubuntu@ubuntu:~$ ll /dev/hda1
brw-rw---- 1 root disk 3, 1 2007-04-14 13:08 /dev/hda1
ubuntu@ubuntu:~$ ll /dev/hdb
brw-rw---- 1 root disk 3, 64 2007-04-14 13:08 /dev/hdb
ubuntu@ubuntu:~$ ll /dev/hdb1
brw-rw---- 1 root disk 3, 65 2007-04-14 13:08 /dev/hdb1
ubuntu@ubuntu:~$ ll /dev/hdb2
brw-rw---- 1 root disk 3, 66 2007-04-14 13:08 /dev/hdb2
ubuntu@ubuntu:~$ ll /dev/hdb5
brw-rw---- 1 root disk 3, 69 2007-04-14 13:08 /dev/hdb5


==================================
I can't find the grub  folder (possible because I boot from live CD?)

ubuntu@ubuntu:~$ less /boot/grub/menu.lst
/boot/grub/menu.lst: No such file or director

==================================
sudo fdisk -l shows the following output:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4678    37576003+  83  Linux
/dev/hdb2            4679        4865     1502077+   5  Extended
/dev/hdb5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   42  SFS


==================================

/etc/fstab is the following
buntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by confused57 on 2007-04-14
Here's a guide for mounting your Ubuntu root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

It would be something like this:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hdb1 /media/ubuntu
```

then to access your configuration files:
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
gksudo gedit /media/ubuntu/boot/grub/device.map
gksudo gedit /media/ubuntu/etc/fstab
```

---

