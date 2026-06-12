---
title: "&quot;initramfs&quot; error"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by tim.hoeffel on 2012-07-23
I installed a dual boot system (with a little help) on one of my HD's  (200GB). My other HD (1TB) has all my files on it and a busted version  of ubuntu 11.10. (the application updater hung on me while trying to  upgrade to 12.04 and made the OS unuseable, hence the dual boot system).  I unplugged the TB drive while installing the OS's to make sure I kept  all my files. But now the TB drive will not boot even though the drive  with the OS's does, but only without the TB drive plugged in. When I try  to boot with the TB drive plugged in I end up with this error message,  "BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash) Enter  'help' for a list of built-in commands. (initramfs)" Entering help isn't  helpful, just a screen of jibberish. Any help on getting my files back  would be appreciated.

---

### Post by dino99 on 2012-07-23
each time a device is plugged/unplugged, the previous uuid is resetted causing this error as it cant find the good uuid.

how to know about the real uuids:  sudo blkid
then set fstab accordingly:  gksu gedit /etc/fstab

:P

---

### Post by tim.hoeffel on 2012-07-23
Thanks so much for your response dino 99,
Results for sudo blkid:
/dev/sda1: LABEL="System Reserved" UUID="E4D4030BD402E022" TYPE="ntfs" 
/dev/sda2: UUID="881C8FF11C8FD918" TYPE="ntfs" 
/dev/sda5: UUID="a20d983b-3d30-4294-8318-250187a25ca2" TYPE="ext4" 
/dev/sda6: UUID="91111d00-21d6-4e72-a50a-3a4084930982" TYPE="ext4" 
/dev/sda7: UUID="a83288bc-e3e3-41fd-bc76-3540c08e86e8" TYPE="ext4" 
/dev/sda8: UUID="8f97bb53-7b46-4482-9f92-594495ceb7a4" TYPE="swap"

sda1 and 2 are the windows partition. I followed directions for setting up the ubuntu partitions. I don't know what the other stuff you mentioned is, but it's terminal commands proceeded by "sudo"?

---

### Post by Shadius on 2012-07-23
> **tim.hoeffel said:**
> Thanks so much for your response dino 99,
Results for sudo blkid:
/dev/sda1: LABEL="System Reserved" UUID="E4D4030BD402E022" TYPE="ntfs" 
/dev/sda2: UUID="881C8FF11C8FD918" TYPE="ntfs" 
/dev/sda5: UUID="a20d983b-3d30-4294-8318-250187a25ca2" TYPE="ext4" 
/dev/sda6: UUID="91111d00-21d6-4e72-a50a-3a4084930982" TYPE="ext4" 
/dev/sda7: UUID="a83288bc-e3e3-41fd-bc76-3540c08e86e8" TYPE="ext4" 
/dev/sda8: UUID="8f97bb53-7b46-4482-9f92-594495ceb7a4" TYPE="swap"

sda1 and 2 are the windows partition. I followed directions for setting up the ubuntu partitions. I don't know what the other stuff you mentioned is, but it's terminal commands proceeded by "sudo"?

For the second command that the previous user mentioned, you'd just enter it as: 
```
gksu gedit /etc/fstab
```

It will ask you for your password and it opens up Gedit to edit the *fstab* file.

Here's a link on [fstab]("https://help.ubuntu.com/community/Fstab").

---

### Post by tim.hoeffel on 2012-07-23
> **Shadius said:**
> For the second command that the previous user mentioned, you'd just enter it as: 
```
gksu gedit /etc/fstab
```It will ask you for your password and it opens up Gedit to edit the *fstab* file.

Here's a link on [fstab]("https://help.ubuntu.com/community/Fstab").

Here is the output from fstab file:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=91111d00-21d6-4e72-a50a-3a4084930982 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=a20d983b-3d30-4294-8318-250187a25ca2 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=a83288bc-e3e3-41fd-bc76-3540c08e86e8 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=8f97bb53-7b46-4482-9f92-594495ceb7a4 none            swap    sw              0       0

Here's what I don't understand. How is the drive going to get mounted if I can not access Ubuntu when I boot with it plugged in? There is also an option in Disk utility for Mount Disk. What will that do?

---

### Post by tim.hoeffel on 2012-07-24
HELP PLEASE! I need to get my files back!

---

