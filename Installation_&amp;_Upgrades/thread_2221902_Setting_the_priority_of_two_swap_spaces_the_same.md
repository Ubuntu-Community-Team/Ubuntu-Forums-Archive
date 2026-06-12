---
title: "Setting the priority of two swap spaces the same"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by baseline2 on 2014-05-04
Hi their,

I have recently installed the desktop ubuntu 12.04.4 version on two harddisks. I have made the root partition Raid-0 on the first harddrive i made a boot partition and one swap partition. On the other harddisk i also made one swap partition. I didn set the two swap spaces in Raid-0 as i heard that is not a smart way to do. On the other hand i read something about setting up the way the two swap spaces are handeled. Normaly they have different priorities and you can set them in /etc/fstab as the same. So i tried and set it to pri=1 but when when i typed in terminal swapon -s this is my output:
 
Filename                                        Type                               Size             Used                          Priority
/dev/sda1                               partition    975868    70220                    -1
/dev/sdb1                               partition    975868    0                                                       -2

How is it possible ubuntu hasn´t changed the way i set the priority sheme? I dit it by the way with the following command sudo gedit /etc/fstab and this is my output:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=dae7dba8-0d03-4689-94a1-66fe900d960a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=e3874b8b-3a7e-4439-a68a-25a44185def0 /boot           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=bdf77fd2-0198-4bc0-8a25-cd2d0e5994a1                 swap    sw, pri=1         0       0
# swap was on /dev/sdb1 during installation
UUID=6162cda1-371f-4478-ae7b-ed222aba1379                 swap    sw, pri=1         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

