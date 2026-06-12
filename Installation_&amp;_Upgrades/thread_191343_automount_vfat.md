---
title: "automount vfat"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by bazder on 2006-06-07
Hi,

I'd like users to be able to read/write an automounted vfat partition on a dual boot machine. Right now the vfat partition automounts and users can read but only root can write to it.  How can I fix this?

thanks,

---

### Post by Robgould on 2006-06-07
You have to edit your /etc/fstab entry for that partition.
 
Read the fstab link in my signature.

---

### Post by pnael on 2006-06-07
Hello,

It is a mount option. You can use :
mount -t vfat /dev/xxx /mnt -o uid=<id of the user>,gid=<group of the user>

man mount will help you.
Once it works. You add the need option to your /etc/fstab file.
Cheers
Philippe

---

### Post by titus1950 on 2006-06-07
[QUOTE=bazder]Hi,

I'd like users to be able to read/write an automounted vfat partition on a dual boot machine. Right now the vfat partition automounts and users can read but only root can write to it.  How can I fix this?

thanks,[/QUOTE]


Read this,it is very helpfull...

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by aysiu on 2006-06-07
[QUOTE=titus1950]Read this,it is very helpfull...

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)[/QUOTE]
It's helpful if the mount point doesn't already exist and if the user is using Gnome and not KDE or XFCE.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bazder on 2006-06-07
yup! working...

thanks to all  :p

---

