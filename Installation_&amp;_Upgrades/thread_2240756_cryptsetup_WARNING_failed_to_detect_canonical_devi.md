---
title: "cryptsetup: WARNING: failed to detect canonical device of /dev/sda1"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by we7master on 2014-08-22
I've been trying to upgrade to 14.04 and so after far numerous problems I've finally got it to boot up. But when I did an update using:-

```
sudo apt-get clean 
sudo apt-get update 
sudo apt-get dist-upgrade 

```

I got the following errors:-

```
cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab

```

Here's the content of my fstab file

```
chris@chris:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f92add46-baed-461a-9bdb-0759f3b19a9b none            swap    sw              0       0
```

Also:-

```
chris@chris:~$ sudo blkid
[sudo] password for chris: 
/dev/sda1: UUID="f4fa3268-d587-411d-81d5-5a9c2f7922cf" TYPE="ext4" 
/dev/sda5: UUID="f92add46-baed-461a-9bdb-0759f3b19a9b" TYPE="swap" 

```

Since getting the errors I been too scared to do a reboot as I don't have another PC to search errors. 

I'm not sure what move to make next.

I searched and found various discussions on the topic but none relating to a 14.04 upgrade.

Thanks for any suggestions, much appreciated.

Kerry

---

