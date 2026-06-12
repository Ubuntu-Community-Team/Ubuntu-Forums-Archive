---
title: "Having GRUB issues with RAID disks"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by krasenpaskaa on 2008-06-05
Hi,

I am having some serious issues getting ubuntu to work.

What I have:

2 x 150gb WD Raptor Drives
1x 750 GB Seagate drive

What I have done:

I made my partitions on my two WD drives exactly as suggested by this post:
[http://ubuntuforums.org/showpost.php?p=4923647&postcount=5](http://ubuntuforums.org/showpost.php?p=4923647&postcount=5)

I was later asked if I wanted to install GRUB on my MBR, I chose to do so.
Everything seemed fine but what happens when I boot is that I get to the screen that says:

GRUB loading, please wait....

And then nothing happens

I have now booted from the Live CD. If I do fdisk -l, I get this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000580e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+  83  Linux
/dev/sda2              17         125      875542+  82  Linux swap / Solaris
/dev/sda3             126        1341     9767520   fd  Linux raid autodetect
/dev/sda4            1342       18241   135749250   fd  Linux raid autodetect

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d3e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+  82  Linux swap / Solaris
/dev/sdb2             123        1338     9767520   fd  Linux raid autodetect
/dev/sdb3            1339       18241   135773347+  fd  Linux raid autodetect

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a4a4a4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       91202   732572672    7  HPFS/NTFS


Can anyone please help me figure out what is wrong here?

---

### Post by dstew on 2008-06-05
When you set up your installation, did you have it like this?:

/dev/sda1 for /boot
/dev/sda2 for swap
/dev/md0 (which is /dev/sda3 and /dev/sdb2) for /
/dev/md1 (which is /dev/sda4 and /dev/sdb3) for /home

Is this the way you set it up? In other words, your /boot directory is on an un-RAIDed partition, correct?

---

### Post by krasenpaskaa on 2008-06-05
> **dstew said:**
> When you set up your installation, did you have it like this?:

/dev/sda1 for /boot
/dev/sda2 for swap
/dev/md0 (which is /dev/sda3 and /dev/sdb2) for /
/dev/md1 (which is /dev/sda4 and /dev/sdb3) for /home

Is this the way you set it up? In other words, your /boot directory is on an un-RAIDed partition, correct?

Yes, it is set up exactly like that

---

### Post by dstew on 2008-06-05
My guess is that grub is mis-installed, such that the boot loader is looking for its stage2 file in one of the RAIDed disks, and to grub this looks like corruption, so it hangs.

Just to check, boot a Live CD, and mount your /dev/sda1 partition. List the root directory. Are the kernel images there? Is the grub directory there? If so, enter the grub directory and list its contents. Is stage2 and menu.lst there? If all this checks out, we only need to re-install the grub boot loader. If the grub directory and files are not there, we have more difficult problems to solve.

---

### Post by krasenpaskaa on 2008-06-05
> **dstew said:**
> My guess is that grub is mis-installed, such that the boot loader is looking for its stage2 file in one of the RAIDed disks, and to grub this looks like corruption, so it hangs.

Just to check, boot a Live CD, and mount your /dev/sda1 partition. List the root directory. Are the kernel images there? Is the grub directory there? If so, enter the grub directory and list its contents. Is stage2 and menu.lst there? If all this checks out, we only need to re-install the grub boot loader. If the grub directory and files are not there, we have more difficult problems to solve.

ubuntu@ubuntu:/test$ ls
abi-2.6.24-16-generic             lost+found
config-2.6.24-16-generic          memtest86+.bin
grub                              System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak



ubuntu@ubuntu:/test/grub$ ls
default        fat_stage1_5       menu.lst           stage1
device.map     installed-version  minix_stage1_5     stage2
e2fs_stage1_5  jfs_stage1_5       reiserfs_stage1_5  xfs_stage1_5



so yeah, it all seems to be there. I am still clueless on what to try next though :)
EDIT: Oh and yeah.. I tried redoing the whole procedure and it is even worse now. All I see when the computer starts is "GRUB", nothing more.

---

### Post by krasenpaskaa on 2008-06-05
Noone got any ideas? Feels like I've tried everything there is by now, starting to suspect hardware problems

---

### Post by dstew on 2008-06-05
It is possible that the disk has errors. Run fsck on the partition:```
sudo fsck /dev/sda1
```. Are the Raptors SATA drives or PATA (IDE) drives? If IDE, check the cables, make sure the drives are correctly jumpered. If they are SATA drives, there is nothing to check.

---

### Post by krasenpaskaa on 2008-06-06
I have tried about 19 different walkthroughs and fixes that I have found now, but nothing will work.

I am going to start over clean.
I have the two 150GB Drives that I want the system on,
and I have the 750G drive with data on it that I want to keep.
All 3 drives are SATA drives

What do I do? Everything I have tried so far makes me unable to boot, Im open to any suggestion

---

### Post by dstew on 2008-06-06
Go ahead and try again. Are you using the Alternate Install CD? I noticed that your two partitions for md1 were not exactly the same size, but I suppose this does not make any difference.

What was strange about your problem was that grub did not get as far as loading the stage2 or menu from the un-RAIDed /dev/sda1 partition. Grub behaved as though the /dev/sda1 directory or file structure was corrupted.

Did you try to just re-install grub? That is, from the live CD, get a grub command line and do```
find /grub/stage2
```Note since you have a boot partition the **find** command should look in the root directories of the partitons for the grub folder. Then, whatever the find command returns, use as the argument for a root statement:```
root (hd0,0)
```Then, setup grub in the MBR of the boot disk with```
setup (hd0)
quit
```Shut down the Live CD system, remove the CD and reboot. You should at least get a menu.

---

### Post by krasenpaskaa on 2008-06-06
> **dstew said:**
> Go ahead and try again. Are you using the Alternate Install CD? I noticed that your two partitions for md1 were not exactly the same size, but I suppose this does not make any difference.

What was strange about your problem was that grub did not get as far as loading the stage2 or menu from the un-RAIDed /dev/sda1 partition. Grub behaved as though the /dev/sda1 directory or file structure was corrupted.

Did you try to just re-install grub? That is, from the live CD, get a grub command line and do```
find /grub/stage2
```Note since you have a boot partition the **find** command should look in the root directories of the partitons for the grub folder. Then, whatever the find command returns, use as the argument for a root statement:```
root (hd0,0)
```Then, setup grub in the MBR of the boot disk with```
setup (hd0)
quit
```Shut down the Live CD system, remove the CD and reboot. You should at least get a menu.

Hi,

I was informed that one of the problems could be that I had the drives set up as RAID in my bios, so I disabled all that now and installed from the alternate CD and set it up like the softwareRAID guide suggests. However, the installer couldnt install GRUB no matter what I do, so I chose to proceed without a boot loader, and here I am again, loaded from Live CD

If I do the find grub thing, I get Error 15: File not found

This is what fdisk -l returns:
```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008c07c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         486     3903763+  82  Linux swap / Solaris
/dev/sda2   *         487       18241   142617037+  fd  Linux raid autodetect

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e87b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         486     3903763+  82  Linux swap / Solaris
/dev/sdb2   *         487       18241   142617037+  fd  Linux raid autodetect

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a4a4a4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       91202   732572672    7  HPFS/NTFS

```

---

### Post by dstew on 2008-06-06
So, you may actually have a FakeRaid controller, if you find BIOS settings that have to do with a RAID. If you want to do pure software RAID, which is what you have been trying to do, you have to be sure the BIOS settings are for no RAID. If you want to do FakeRaid, that is different. You set it up in the BIOS, and use the dmraid program to detect and use the array, and install Ubuntu by hand, because the installer cannot deal with dmraid. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto").

Looking at your new setup, you do not have an un-RAIDed boot partition. Grub cannot detect files on software RAID partitions, except by accident in some RAID-1 arrays (mirrored).

Why not try a plain install just for fun, no RAID, to see if you can get Ubuntu into a partition? If that works, create a software RAID as a spare disk, and see if Ubuntu can set it up and access it.

---

### Post by krasenpaskaa on 2008-06-06
> **dstew said:**
> So, you may actually have a FakeRaid controller, if you find BIOS settings that have to do with a RAID. If you want to do pure software RAID, which is what you have been trying to do, you have to be sure the BIOS settings are for no RAID. If you want to do FakeRaid, that is different. You set it up in the BIOS, and use the dmraid program to detect and use the array, and install Ubuntu by hand, because the installer cannot deal with dmraid. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto").

Looking at your new setup, you do not have an un-RAIDed boot partition. Grub cannot detect files on software RAID partitions, except by accident in some RAID-1 arrays (mirrored).

Why not try a plain install just for fun, no RAID, to see if you can get Ubuntu into a partition? If that works, create a software RAID as a spare disk, and see if Ubuntu can set it up and access it.

So could I for example install from Live CD, make a 10gb / partition and a 6gb swap or something, and then use the remaining   134GB to make a raid with the other 150GB drive?

---

### Post by krasenpaskaa on 2008-06-06
Ok no I couldnt. That didnt work either. All that showed up when I booted was "GRUB". Nothing else

---

### Post by dstew on 2008-06-06
Yes, like that. Only just give swap 1 Gb. You can leave the rest of the disks unallocated, and later make two equal size ext3 partitions for a RAID with a partition editor like GParted. Use the mdadm program from within Ubuntu to set up the RAID devices.

It also occurred to me, if your most recent install was on a RAID-1, and you tried to install grub using the instructions I gave above, you would have to change the find command argument to /boot/grub/stage2 because now you do not have a separate /boot partition. But, if the RAID is a type 0 or 5, grub cannot find anything on that.

---

### Post by dstew on 2008-06-06
So you could not get grub to work even after doing a plain install to an un-RAIDed partition?

---

### Post by krasenpaskaa on 2008-06-06
> **dstew said:**
> So you could not get grub to work even after doing a plain install to an un-RAIDed partition?

No, same problem as before. It just wont boot.

---

### Post by krasenpaskaa on 2008-06-06
Ok now I managed to get a working install by just selecting Guided Install on one of my Raptor Drives.

So now it's working I guess, but I still don't have my raid.

---

