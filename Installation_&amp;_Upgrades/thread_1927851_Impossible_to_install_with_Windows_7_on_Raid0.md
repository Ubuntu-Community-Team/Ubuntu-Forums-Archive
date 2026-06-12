---
title: "Impossible to install with Windows 7 on Raid0"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by adrienm001 on 2012-02-18
Hello !

Since yesterday I'm trying to install Unbuntu 11.10 on my laptop which is a Vaio VCPZ1 (with Raid0). In fact, I can install Ubuntu but at the end I'm only able to boot on Ubuntu from GRUB but I just can boot Windows.

Every time I restore my laptop to factory configuration but I can make it work. :(

In fact, while I have factory settings, I have 3 partitions : the first one for the restoration, the second is the hidden Windows partition and the last one is my Windows installation partition.

I want to create Ubuntu own partition so I just reduce the Windows main partition to release 20 Go. While I'm trying to install Ubuntu, I just create a new ext4 partition for Ubuntu but the problem comes from the boot sector. Every time I get an error except when I choose the small Windows hidden partition as boot sector.
So I do, I can only boot on Ubuntu and when I repair Windows boot sector, neither Ubuntu neither Windows can boot.

Can someone help me ?

PS : sorry for the English mistakes but it's not mother tongue.

---

### Post by darkod on 2012-02-19
Can you boot ubuntu in live mode (Try Ubuntu) and post the results of:
sudo fdisk -l (small L)

Lets see what type of partitions do you have.

The problem might be if you are using the standard desktop cd. For raid installation you should use the alternate install cd, it works better, especially when installing the bootloader. That might be your issue.

But lets see how the partitions look first.

---

### Post by adrienm001 on 2012-02-19
Hello !

Thank you for your answer ! This is what I get while I'm typing your command :
```

Disk /dev/sda: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    15794175     7897056+   b  W95 FAT32

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b78808a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    16691199     8344576   27  Hidden NTFS WinRE
/dev/sdb2   *    16691200    16895999      102400    7  HPFS/NTFS/exFAT
/dev/sdb3        16896000   209119231    96111616    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/mapper/isw_cgfdijdiie_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x2b78808a

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfdijdiie_Volume0p1            2048    16691199     8344576   27  Hidden NTFS WinRE
/dev/mapper/isw_cgfdijdiie_Volume0p2   *    16691200    16895999      102400    7  HPFS/NTFS/exFAT
/dev/mapper/isw_cgfdijdiie_Volume0p3        16896000   209119231    96111616    7  HPFS/NTFS/exFAT

Disk /dev/mapper/isw_cgfdijdiie_Volume0p1: 8544 MB, 8544845824 bytes
255 heads, 63 sectors/track, 1038 cylinders, total 16689152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x4d544f4f

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfdijdiie_Volume0p1p1   ?   218137203  2138359164   960110981   70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p1p2   ?   544370800  2464669663   960149432   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p1p3   ?   225600882   769746299   272072709   82  Linux swap / Solaris
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p1p4   ?  2760638474  2760690110       25818+  61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_cgfdijdiie_Volume0p2: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x4d544f4f

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfdijdiie_Volume0p2p1   ?   218137203  2138359164   960110981   70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p2p2   ?   544370800  2464669663   960149432   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p2p3   ?   225600882   769746299   272072709   82  Linux swap / Solaris
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p2p4   ?  2760638474  2760690110       25818+  61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_cgfdijdiie_Volume0p3: 98.4 GB, 98418294784 bytes
255 heads, 63 sectors/track, 11965 cylinders, total 192223232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x4d544f4f

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfdijdiie_Volume0p3p1   ?   218137203  2138359164   960110981   70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p3p2   ?   544370800  2464669663   960149432   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p3p3   ?   225600882   769746299   272072709   82  Linux swap / Solaris
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p3p4   ?  2760638474  2760690110       25818+  61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

```

I have just done a factory restoration and I have already reduced my Windows main partition.

Thanks for your help

---

### Post by darkod on 2012-02-19
I guess it looks fine.

One question: Are you aware how RAID0 works? That your data is in danger if one disk fails? With raid0 you lose all data if one disk fails, you can't recover it even if the other disk is fine.

Apart from that, try installing ubuntu with the alternate install cd, I think grub will install fine with it.

---

### Post by adrienm001 on 2012-02-19
Ok, thank you for your help :)

I'm downloading the alternate install cd. For your question, I know that if one of the disks fails I lose everything but I only use this computer for my deplacement so I always have a back up of these files.

---

### Post by buckeyered80 on 2012-02-19
You can make it work with the alternate cd. I have a RAID-capable system too, but I had to disable the RAID. It was causing all kinds of issues with Ubuntu...I am not sure why. If you can't make it work with the alternate CD, you can uninstall the OS RAID from Ubuntu before you install. I did this by this command ```
sudo apt-get remove dmraid
```

But, of course, do not do this unless you don't want RAID.

---

### Post by adrienm001 on 2012-02-19
In fact I would like to keep my Raid0.

But now I've exactly the same problem as before. I'm still installing Ubuntu and I get an error while I have to choose where to install GRUB. I've tried /dev/mapper and /dev/sda but it doesn't work :(

---

### Post by adrienm001 on 2012-02-19
Finally I've finished the installation without GRUB. After this, I reboot my computer and I got an error from GRUB. So I boot on my Windows cd to repair Windows MBR.

So now, my Windows is working. Do you know what can I do to make Ubuntu worked ?

---

### Post by darkod on 2012-02-19
You can try adding grub from live mode. In live mode it should recognize the raid array because it is loading the dmraid package.

If you can post the fdisk results again now after ubuntu is installed, I can try to help with commands to install grub2.

---

### Post by adrienm001 on 2012-02-21
Thank you :D

This is what I get while I'm typing fdisk in terminal now :
```

Disk /dev/sda: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    15794175     7897056+   b  W95 FAT32

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2b78808a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    16691199     8344576   27  Hidden NTFS WinRE
/dev/sdb2   *    16691200    16895999      102400    7  HPFS/NTFS/exFAT
/dev/sdb3        16896000   209119231    96111616    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/mapper/isw_cgfdijdiie_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x2b78808a

                              Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfdijdiie_Volume0p1            2048    16691199     8344576   27  Hidden NTFS WinRE
/dev/mapper/isw_cgfdijdiie_Volume0p2   *    16691200    16895999      102400    7  HPFS/NTFS/exFAT
/dev/mapper/isw_cgfdijdiie_Volume0p3        16896000   209119231    96111616    7  HPFS/NTFS/exFAT

Disk /dev/mapper/isw_cgfdijdiie_Volume0p1: 8544 MB, 8544845824 bytes
255 heads, 63 sectors/track, 1038 cylinders, total 16689152 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x4d544f4f

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfdijdiie_Volume0p1p1   ?   218137203  2138359164   960110981   70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p1p2   ?   544370800  2464669663   960149432   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p1p3   ?   225600882   769746299   272072709   82  Linux swap / Solaris
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p1p4   ?  2760638474  2760690110       25818+  61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_cgfdijdiie_Volume0p2: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfdijdiie_Volume0p2p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p2p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p2p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p2p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_cgfdijdiie_Volume0p3: 98.4 GB, 98418294784 bytes
255 heads, 63 sectors/track, 11965 cylinders, total 192223232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x4d544f4f

This doesn't look like a partition table
Probably you selected the wrong device.

                                Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cgfdijdiie_Volume0p3p1   ?   218137203  2138359164   960110981   70  DiskSecure Multi-Boot
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p3p2   ?   544370800  2464669663   960149432   74  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p3p3   ?   225600882   769746299   272072709   82  Linux swap / Solaris
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cgfdijdiie_Volume0p3p4   ?  2760638474  2760690110       25818+  61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order


```

---

### Post by darkod on 2012-02-21
Those results look very confusing to me. Or I don't understand them.

The three partitions listed on /dev/mapper/blahblah_Volume0 are one hidden and two ntfs partitions. No sign of linux partitions.

There should be Linux type partition on it, but I can't seem to see it.

---

### Post by adrienm001 on 2012-02-21
Yes it's so strange...

I can't see it at the begining but at the end it appears :(

Maybe I have installed wrong but that's strange.

---

### Post by adrienm001 on 2012-02-21
I retry to install Ubuntu with the alternate cd and effectively I did something wrong yesterday.

I did it again today and now it seems that the installation worked. After the reboot I repaired Windows boot sector again and I reboot from a live cd. I tried typing the command "sudo fdisk -l" again but I got an error this time :
```

fdisk: unable to seek on /dev/sda: Invalid argument

```

So I try to see on gparted how is my hdd and this is what I get. During the installation earlier I still had to skip GRUB installation. Do you think there is a way to install GRUB now ?

---

### Post by darkod on 2012-02-21
OK, at least now it looks better. We can clearly see the ext4 partition, #5.

Yes, grub can be added.

Boot into live mode and try to mount the root partition, type the exact raid device including the /dev/mapper/blahblah ending with Volume0p5.

```
sudo mount /dev/mapper/blahblah_Volume0p5 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/blahblah_Volume0 (without the p5)
```

The first command might return an error, I am not sure if the array is automatically activated in live mode (anyone knows???).

---

### Post by darkod on 2012-02-21
I saw mentioned on google that some people had success installing grub1 and not grub2. But lets give grub2 a chance first with the above commands, and later you can try grub1 if you feel up to it.

---

### Post by adrienm001 on 2012-02-22
Ok, I just tried the commands above and I got no error even with the first one. The only message I got is when I type the second one :
```

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet;  avoiding it.  This software may cause boot or other problems in future.   Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

```

But when I reboot, I get something like a console. Do you know what is it ?

---

### Post by darkod on 2012-02-22
If you google that warning, I found this:
> I had no idea what flexnet is.

[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)

The problem turned out to be Adobe's digital rights management software   [DRM].  Do your own search for "FlexNet," formerly known as "SafeCast."    What I have read is that FlexNet is a viral rootkit that replicates  in  multiple locations whenever a CS3 or CS4 product is installed,  including  trial versions.  

Once something like this is installed you are trapped. The above link discusses the zero out of everything and reinstall.

Be careful if the only solution discussed is to zero out the disk/array. That would delete all data on it.

---

### Post by adrienm001 on 2012-02-22
Yes that's strange because I dont' have any Adobe's product except Adobe Reader.

In my university there is a group of students who can help other sudents to install Ubuntu, I think I'll go on Monday. If you want I can try to explain you what is the problem after seeing them :)

---

### Post by darkod on 2012-02-22
If you find a solution, it would definitely be best if you post it. Other people have similar problems and the threads show up in google too.

One thing we didn't try is grub1. As I said, I saw one reference that grub1 might work.

If you want, you can try it but you need to enter your install with chroot. It would be like:
Mount preparing for chroot:
```
sudo mount /dev/mapper/blahblah_Volume0p5 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev /mnt/dev
sudo chroot /mnt
```Remove grub2 completely and install grub1:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub
update-grub (if asked to create menu.lst say yes)
grub-install /dev/mapper/blahblah_Volume0 (without p5)
```Exit chroot and unmount:
```
exit
sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt
```Restart and keep fingers crossed. :) If that doesn't work let us know what happens, there is one other variation of the commands. This is the shorter one and I hope it works.

---

### Post by adrienm001 on 2012-02-23
Ok, I'll try to do every thing but I've a problem when I'm trying to install GRUB : I got this error message :
```

Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 Package grub is not available, but is referred to by another package.
 This may mean that the package is missing, has been obsoleted, or
 is only available from another source
 E: Package grub has no installation candidate

```

I searched on google and I found that in chroot, the internet connection might not work :s
By the way, I have a SuperGrub Disk. Do you think it might be insteresting to install GRUB using it ?

---

### Post by darkod on 2012-02-23
Uhhh I have never touched SG. I can't say yes or no.

---

