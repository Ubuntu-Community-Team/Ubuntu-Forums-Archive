---
title: "Ubuntu filesystem Error"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by georgeep on 2008-09-05
mount: Mounting /dev/sda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or
directory
mount: Mounting /dev on /root/dev failed:No such file or directory
Target filesystem doesn't have /sbin/init

This is the problem my server is giving and i can get pass the last line

Please i need this help argently to save all my web content:
Now i have done this with a live CD but still nothing

sudo mount -t ext3 -o rw /dev/hda1 /mnt
sudo chroot /mnt
sudo apt-get update; apt-get upgrade; apt-get install udev

I can't get the system to upgrade

---

### Post by manishtech on 2008-09-05
Try mounting it as ro , atleast for the time being
```
sudo mount -t ext3 -o ro /dev/hda1 /mnt
```

Can you paste the contents of /etc/fstab?

---

### Post by Crafty Kisses on 2008-09-05
It wouldn't hurt to see sudo fdisk -l either.

---

### Post by georgeep on 2008-09-06
Hello Manishtech,

This is the contents of /etc/fstab

root@ubuntu:~# cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

Also for fdisk -l

root@ubuntu:~# sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9639    77425236   83  Linux
/dev/sda2            9640        9729      722925    5  Extended
/dev/sda5            9640        9729      722893+  82  Linux swap / Solaris

Then for sudo blkid

root@ubuntu:~# sudo blkid
/dev/sda1: LABEL="/" UUID="4a6ee132-6a71-4288-8a09-479f7257d04e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap"

These are all the information in my hdd

Pls see what you can do to help my filesystem Error

thanks


mount: Mounting /dev/sda1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/ .static/dev failed: No such file or
directory
mount: Mounting /dev on /root/dev failed:No such file or directory
Target filesystem doesn't have /sbin/init

---

### Post by caljohnsmith on 2008-09-06
From the Live CD, try:
```
sudo umount /dev/sda1  [COLOR="Blue"][just to make sure you don't have it mounted anywhere else][/COLOR]
sudo fsck /dev/sda1
```
If fsck reports any errors, be sure to say "y" when it asks to fix them. Let us know how that goes.

---

