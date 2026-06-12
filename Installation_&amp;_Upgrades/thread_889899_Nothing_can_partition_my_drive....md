---
title: "Nothing can partition my drive..."
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by Legomaniac25 on 2008-08-14
Hey everyone,

I had a post simmilar to this a few weeks ago, but I have finnaly got enough motivation to try to fix it again. Please don't regard this as a dupe thread however, as my problem has now expanded.

No matter what I try I can't seem to partition my hard drive. I tried the windows tool, the automatic partitioner in ubuntu install, GParted in the Ubuntu live cd and GParted in a special distro of linux made specifically for partitioning and data management called PartedMagic. (Which I have used before successfully on this exact drive)

All of them fail, and return the message that they cannot continue with the process.

I'm not sure what kind of data sets you guys might need to help me figure out what the issue may be, so I will just post the terminal responses I got when trying to tackle the issue before.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x958c958c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19453   156256191    7  HPFS/NTFS

```

and...

```
ubuntu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
tmpfs                  531M    17M   514M   4% /lib/modules/2.6.24-19-generic/volatile
tmpfs                  531M    17M   514M   4% /lib/modules/2.6.24-19-generic/volatile
varrun                 531M   107k   530M   1% /var/run
varlock                531M      0   531M   0% /var/lock
udev                   531M    50k   530M   1% /dev
devshm                 531M    13k   531M   1% /dev/shm
tmpfs                  531M    17k   531M   1% /tmp
gvfs-fuse-daemon       531M    94M   437M  18% /home/ubuntu/.gvfs
/dev/sda1              161G    97G    64G  61% /media/disk

```

Thanks in advance once again for all your assistance.

---

### Post by logos34 on 2008-08-14
try all the suggestions here (applies to desktops as well):
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by ezsit on 2008-08-15
What are you attempting to do? Do you want to wipe the partitions and start from scratch? Did you want to try to shrink the NTFS partition and add Linux?

Your error message is quite vague and you really do not say what exactly you tried. Some possible suggestions may be:

1. boot from a live cd
2. open a terminal
3. type "sudo fdisk -l"
4. make sure the drive is not mounted, type "sudo umount /dev/sda1"
5. use cfdisk by typing "sudo cfdisk /dev/sda1"
6. remember to write the changes to disk before quitting cfdisk

I have never had cfdisk fail me yet.

Alternatively, if you know the brand of hard drive, go to the manufacturer's website and download the utilities they provide to install and partition the hard drive. Use the manufacturer's utility to wipe (or zero out) the entire hard drive and run diagnostics to find out if the hard drive is failing.

---

