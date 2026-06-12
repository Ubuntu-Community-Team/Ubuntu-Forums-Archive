---
title: "GRUB installation (dual boot + raid0)"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by keltu on 2007-08-22
im installing Ubuntu 7.04 by this guide
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

i stop at this point , i got confused..

> Next, tell GRUB where all the stuff is that is needed for the boot process:

**root (hd0,4)**

/!\ This is one of the most common sources of error, so we will explain this in excruciating detail. From GRUB's perspective, "root" is whatever partition holds the contents of /boot. For most people, this is simply your linux root (/) partition. E.g., if / is your 2nd partition on the RAID you indicated above as hd0, you would say "root (hd0,1)". Remember that GRUB starts counting partitions at 0. The first partition is 0, the second is 1, and so on. In my case, however, I have a separate boot partition that GRUB mounts read-only for me at boot time (which helps keep it secure). It's my 5th partition, so I say "root (hd0,4)"

So, if I have a system where /dev/mapper/via_x array has been partitioned so that /dev/mapper/via_x1 is going to be / and /dev/mapper/via_x2 will be /boot I need to type the following because /boot is mounted on the second partition of array hd0

[b]device (hd0) /dev/mapper/via_x
root (hd0,1)[/b]

If I only have one non-swap partition, /dev/mapper/via_x1 that is going to be / and no separate /boot, the /boot folder will be on this partition, so
[b]
device (hd0) /dev/mapper/via_x
root (hd0,0)[/b]


this is how my RAID partitions looks like
> ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "nvidia_heiifefe" already active
RAID set "nvidia_heiifefe1" already active
RAID set "nvidia_heiifefe5" already active
RAID set "nvidia_heiifefe6" already active
RAID set "nvidia_heiifefe7" already active
RAID set "nvidia_heiifefe8" already active


1,5,6,7 are windows NTFS partitions
7 is main ext3 linux partition, its where i want (/)
8 is swap partition

i have 2 disks in raid0

> ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_heiifefe", stripe, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_heiifefe", stripe, ok, 312581806 sectors, data@ 0


fdisk -l
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10230    82172443+   7  HPFS/NTFS
/dev/sda2           10231       38914   230404230    f  W95 Ext'd (LBA)
/dev/sda5   ?       98775      209114   886303817+  75  PC/IX

what i need to type in the bold commands
```
root (hd**0,4**)
```

and
```
device (hd0) **/dev/mapper/via_x**
root (**hd0,0**)
```

please help ;-)

---

