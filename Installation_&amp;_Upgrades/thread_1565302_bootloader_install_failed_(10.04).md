---
title: "bootloader install failed (10.04)"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by unigee on 2010-08-31
Hi,

I have been trying to install Ubuntu 10.04.1 but I am having trouble on the installation.

At 93% of the installation, ubuntu displays an error message "Bootloader install failed" and then it gives me an option to change location. I have tried all three options (it was something like sda1, sda2 - forgive me, but I can't exactly remember what they were) but the result is always "Bootloader install failed"

So the only option I have left is to install without a bootloader (and manually install it) or cancel the installation. Unfortunetely I am not linux savy enough know how to manually install a bootloader.

I am doing a fresh ubuntu install, and choosing the 'use entire hdd' for the partitions as I will not be duel booting to another OS.

Currently, I installed ubuntu 8 without a single problem (beside some driver issues), just so I could register on the forums for assistance.
Almost tempted to upgrade ubuntu 8 to 9.06, then perform another upgrade to get the latest version installed (the only thing thats stopping me is my bandwidth limitation per day)

Any ideas?

Thanks

---

### Post by tommcd on 2010-08-31
How many hard drives are on your system?
Are you installing to an internal or external hard drive?
Do you have anything like a flash drive or external hard drive plugged into the system while you are installing Ubuntu?
Boot from the live CD, open a terminal, and run:
```
sudo fdisk -l
```
This will list your hard drives and partitions.

Also, be sure to run the option "*check disc for defects*" when you boot the 10.04 CD. This will verify that the CD is good. I don't think this is the problem here, although it is always good to rule out a bad CD when an install fails.

If you must install grub2 manually from the 10.04 live CD, follow this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
If you only have 1 hard drive, then grub2 should just install to the MBR of that hard drive.

Note: Installing Ubuntu is not a prerequisite for registering on the Ubuntu forums.

And welcome to the Ubuntu forums!

---

### Post by unigee on 2010-09-01
Thank you for the reply.

1. I have one hard drive on my system
2. This is an internal hd
3. I have no USB devices attached to the computer while install ubuntu
4. my sudo fdisk -l contents
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1983

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60045   482311431   83  Linux
/dev/sda2           60046       60801     6072570    5  Extended
/dev/sda5           60046       60801     6072538+  82  Linux swap / Solaris
```


I will try install this again, and manually install the bootloader from the link you pasted (if it fails again)

I will report back on my progress

Thanks

P.S I seem to have missed the option "*check disc for defects"* on the boot up

---

### Post by wildcat29 on 2010-09-01
I'm having the same problem... new HDD, only one HDD and stops install at 93% and wont  let me install any further. 

I burned the disc from my mac and verified the disk before burning...

here is what I have

[PHP]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035a14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       77074   619095040   83  Linux
/dev/sda2           77075       77826     6034433    5  Extended
/dev/sda5           77075       77826     6034432   82  Linux swap / Solaris [/PHP]

---

### Post by ronparent on 2010-09-01
Complete the install without the boot loader. Then fix it from a live cd session using the section entitled 'Reinstalling Grub 2' from the following as a guide: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Sometimes the installer throws you a quirk in installing the boot loader. The above should allow you to fix it. Good luck.

---

### Post by SuperRook on 2011-04-08
Having the same problem.
I have a T3500 PC with 2 320G SATA drives in a RAID configuration. First I resized Windows XP using GPARTED. Then I installed UBUNTU 10.04 in the open space. When I got to Grub install it failed. None of the options provided worked so I proceeded with install. I then tried to install Grub2 separately per
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
but the first 2 methods failed. I didn't try method 3 CHROOT Any suggestions?
Thanks
ubuntu@ubuntu:~$ sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdd3add3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       50993       77827   215536896    7  HPFS/NTFS
/dev/sda2               1       50993   409600769    5  Extended

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdb doesn't contain a valid partition table

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/mapper/isw_eagajidbdb_01: UUID="42041D09041D0219" TYPE="ntfs" 
/dev/mapper/isw_eagajidbdb_05: UUID="9b67f6cb-b0ee-4992-87dd-1995d4454ff3" TYPE="ext4" 
/dev/mapper/isw_eagajidbdb_06: UUID="9d3cc8b0-1cbc-4c87-a826-e38ca10ede40" TYPE="swap"

---

### Post by ronparent on 2011-04-08
Which is your boot drive? The grub install will fail if you try to install the boot loader to any drive that is a raid component. The failure is not actually fatal and can be fixed by reinstalling grub.

If the raid is your boot drive using the two step method as follows should work:
```
sudo mount /dev/mapper/isw_eagajidbdb_05 /mnt

sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_eagajidbdb_0

```
I am guessing at the name '/dev/mapper/isw_eagajidbdb_0' but you can look in the directory /dev/mapper to verify the actual name. It should be the first one listed after control and represents the link for the raid overall. The other three names represent the partitions on the raid.

---

### Post by SuperRook on 2011-04-12
Thanks ronparent. My pc is now booting into grub. I believe all that remains is setting up grub for multiboot.

---

