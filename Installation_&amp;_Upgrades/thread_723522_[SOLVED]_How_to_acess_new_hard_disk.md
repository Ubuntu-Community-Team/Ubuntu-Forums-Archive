---
title: "[SOLVED] How to acess new hard disk?"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by Anders J on 2008-03-13
I have a clean Gutsy system running on a 500 GB SATA disk. I got myself a second disk, did some reading and managed to get it formated:
```
anders@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ccc13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59688   479443828+  83  Linux
/dev/sda2           59689       60801     8940172+   5  Extended
/dev/sda5           59689       60801     8940141   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002388b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

So far it looks good (I hope...), the disk is there and I think all I have to do is to add something clever to fstab.

I tried adding ```
/dev/sdb1	/media/sdb	ext3	defaults, errors=remount-ro	0	2
``` to fstab, but in spite of reading here and there I do not fully understand if I am supposed to create a mount point directory or what other process should be used to give this second disk an identity. I will use the disk for storage only, there are no plans to make it bootable.

There is already a directory /media/sdb created tonight, did gparted create that for me already?

---

### Post by taurus on 2008-03-13
Personally, I would modify the entry in /etc/fstab for the second harddrive to this.

```
/dev/sdb1  	/media/sdb1	ext3	defaults   0	2
```
Save it.  Now, create the new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
And if you want to write to /media/sdb1 without using sudo, then you need to change the ownership of /media/sdb1 from root to your login name, _assuming_ your login name is **anders**.

```
sudo chown -R **anders**:**anders** /media/sdb1
ls -la /media
```

---

### Post by Anders J on 2008-03-13
Thanks. This is Linux in a nutshell. Some nine months into it, there is still a considerable learning curve, but You get help and advice, always.

At first it didn't quite turned out as expected, but after some examination I found that I called the disk sdb and sdb1 in different locations and as soon as that was resolved it showed up on the desktop as expected.

---

