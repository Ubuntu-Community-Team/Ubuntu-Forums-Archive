---
title: "hosed install, help needed"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by soonindallas on 2006-02-24
I have a laptop that I dual boot with Win XP and Ubuntu.  I split the HD 50/50 initially and had Breezy installed in a single partition.  I wanted to change the install to one similar to the one described in this post: [http://www.ubuntuforums.org/showthread.php?t=133312](http://www.ubuntuforums.org/showthread.php?t=133312)

My HD is 80G.  I wanted to get to roughly:
20G for XP (FAT32)
10G for a Breezy root
10G for a Dapper root
40G for shared /home
1G swap

Here is where I am:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         383     3076416   12  Compaq diagnostics
/dev/hda2   *         384        2938    20523037+   c  W95 FAT32 (LBA)
/dev/hda3            5046        7149    16900380   83  Linux
/dev/hda4            7150        9729    20723850    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris
/dev/hda6            7150        9254    16908349+  83  Linux
/dev/hda7            9255        9267      104391   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$
```

hda3 contains the data from my home folder.  I want to make this a /home partition.

hda6 a copy of the single partition that contained my entire Breezy install.  I want to make this a Breezy root partition.

hda 7 is empty and destined to be a /boot partiton where I would put the grub folder and kernel images as described in the post I cited.

I want to create a Dapper root partition.

I used the Breezy install disk partitioner to change the mount points of the partitions thus:
hda3 /home
hda 6 /
hda7 /boot

but the partitioner exited telling me that I could break my install, so I guess grub is not properly configured.

I can boot Breezy but Gnome won't let me in and tells me that permissions of my .drmc (?) are not correct and should be 644.  I can't open a failsafe Gnome session.

I have gparted live cd, Breezy live cd and Breezy install disk.  Please help me recover.

---

### Post by LordBug on 2006-02-24
I find it odd that you have such huge gaps in your cylinder counts.  2939-5045 and 9268-9541 don't appear to be accounted for?  HDA6 and HDA7 are have lower cylinder positions than HDA5?  These look strange.  These may be why the partioner is exiting.

As for .drmc, there's another thread talking about that.  Try using sudo to run chown and chmod on the file.

---

### Post by soonindallas on 2006-02-24
right, there is some unused space.

hda4 is an extended partition that contains hda5, 6 & 7

---

