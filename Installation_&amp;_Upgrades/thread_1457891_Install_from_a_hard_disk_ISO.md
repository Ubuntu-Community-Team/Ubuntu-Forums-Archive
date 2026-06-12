---
title: "Install from a hard disk ISO"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by bugsvoid on 2010-04-19
Hello all:

I tried the suggestions from different threads here and was sucessful in booting up ubuntu iso from harddisk using grub4dos.

I used following commands at grub4dos prompt:
map (hd0,4)/ubuntu.iso (0xff)
map --hook
kernel /casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso
initrd /casper/initrd.lz

The live system was up and me was happy.

Now I want to get happier. I want to install the system on my harddisk. However when I tried the installer from the live System, it says that a partition is already mounted and can not proceed with installation. As correctly said, the partition was mounted on /isodevice and I can not umount that partition.

So is there any way to install from ISO without burning the CD? I had been successful in booting the Live system but the install has failed. Any pointers?

---

### Post by SnickerSnack on 2010-04-19
No, you cannot install on the partition that contains the iso that you are installing from.

So, maybe your boot disk will let you partition the drive so that you can have one partition separately holding the iso while you install to the other partition(s).  NOTE: This will likely involve resizing partitions and may damage the iso.  I recommend simply burning a cd.

---

### Post by bugsvoid on 2010-04-19
Forgot to mention in the original post, but I have already partitioned my hardisk correctly. The iso is located on a separate partition and another partition is already created for linux installation. The only thing required is to re-format the linux partition before the install. No re-sizing of any partition is required on my hard-disk. The only problem is one of the partition on the same device has my iso, which is now mounted as part of my live system and now I can not unmount it. Hence the installer is not ready to touch the disk.

---

### Post by SnickerSnack on 2010-04-24
What exactly is mounted?  When you say

> **bugsvoid said:**
> one of the partition on the same device has my iso, which is now mounted

I don't know if which refers to partition, device, or iso.

---

### Post by bugsvoid on 2010-04-25
'which' refers to the partition. The partition which has the iso is mounted under /isodevice directory in the live system. Pls refer my original post.

---

### Post by Chaos234 on 2010-05-01
See: [http://ubuntuforums.org/showpost.php?p=7764239&postcount=3](http://ubuntuforums.org/showpost.php?p=7764239&postcount=3)

Basically you need to force the device to unmount... while it is still being used as a root filesystem. sudo umount -l -r -f /isodevice

Ubuntu dropped the ball here. Why would you possibly need to change the partition table... if you are not changing the same partitions?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/313452](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/313452)

---

