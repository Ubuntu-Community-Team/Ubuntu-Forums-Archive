---
title: "Automount -filesystem error"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2006-07-28
Auto mount for USB devices is not working. The device is sda1, mount location is /media/usbdrive (NOT owned by root) I used the following command (NOTE - only linux, fs ext3 only.)

sudo mount -t ext3 /dev/sda1 /media/usbdrive

with the following response

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail

 VFS: Can't find ext3 filesystem on dev sda1

ls -la /dev/sda*
brw-rw---- 1 root plugdev 8, 0 2006-07-28 11:36 sda
brw-rw---- 1 root plugdev 8, 1 2006-07-28 11:36 sda1

So, the 64 th$ questions is - what is the correct mount command to eventually put in /etc/fstab?  I would like to be able to use the memory stick , digital camera and an external HD.

This worked before, but I've installed XGL and other things do not work anymore. Help would be appreciated. THANKS:D

---

### Post by john_spiral on 2006-07-29
run **fdisk -l /dev/sda1** to see what filesystem type the drive has

---

### Post by K.Mandla on 2006-07-29
This might be a dumb question, but are you sure it's ext3? It's not vfat? I think FAT16 is default for USB, flashcards and whatnot, but if you made it ext3 ... that's different.

If it really is ext3 then perhaps ...

```
/dev/sda1 /media/usbdrive ext3 defaults 0 2
```
will work for you in fstab. Otherwise ...

```
/dev/sda1 /media/usbdrive vfat defaults 0 2
```
should work. I might be slightly off on that; I'm at work now and can't check my facts.

---

