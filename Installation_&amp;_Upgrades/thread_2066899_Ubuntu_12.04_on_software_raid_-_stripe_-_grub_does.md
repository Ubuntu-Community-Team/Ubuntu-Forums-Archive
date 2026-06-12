---
title: "Ubuntu 12.04 on software raid - stripe - grub doesn't load"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by sgoranov on 2012-10-05
Hi all,
I'm trying to install ubuntu with windows 7 together on software raid device - stripe. First I installed windows on first partition. Then I created 3 more partitions - 2 ext4 partitions and finally one more ntf partition. I've got no problems with windows - it boots and works correct.
After that I decided to install ubuntu. Installation was ok, I specified the device to install the grub and install was successful. The problem is after reboot the grub is not loaded but directly the windows. Any idea how or where to install grub?
Tanks in advance!

---

### Post by darkod on 2012-10-05
That depends where you selected to install it. If you set a partition as the destination, of course it won't show since the bootloader should be on the MBR. So, it should be on the MBR of the raid device, not on a partition.

Another note, you say software raid but then you say you installed a dual boot. Windows can't recognize linux software raid. Do you actually mean fakeraid (bios raid)?

If this is fakeraid, the above about the array MBR would apply, and it's best to use the Alternate Install CD for ubuntu installation, not the standard live cd.

If it is real linux software raid, using mdadm, the bootloader goes to both disks, not to the array MBR, but as already mentioned, windows wouldn't recognize mdadm raid.

---

### Post by sgoranov on 2012-10-05
It's fake raid - bios raid. Question is where to install the boot loader?

---

### Post by darkod on 2012-10-05
And it's already answered, the Master Boot Record of the array.

The name it gets is something like /dev/mapper/blah_blah... You need to use that as destination for grub. But make sure you don't point it to a partition. Usually the partitions would end in p1, p2, etc.
But they can also end in only a number. Or underscore and number like _1, _2, etc.

Sometimes it's difficult to get the array name since it's not very user friendly and you don't know which letters belong to the partition or not.

If you can't find it you should be able to see it from live mode (if you use the live cd). Sometimes you need to activate the array first with:
sudo dmraid -ay

If you use the Alternate Install CD it will tell you the exact device name in the manual partitioning section.

---

### Post by sgoranov on 2012-10-06
Thanks! Will try again to install the grub.

---

### Post by sgoranov on 2012-10-06
Result is the same - grub does not appear but instead windows is loaded directly. I installed the boot loader on  /dev/mapper/ddf1_raid02. Wondering why I've got ddf1_raid02 but not ddf1_raid01? Anyway in this way it doesn't boot.
After that decided to use the alternate CD. It's is not capable to load required drivers because the device was not shown. Other suggestions are welcome!

P.S. I have to note once again - I've got software raid - stripe. It's bios raid with AMD motherboard.

---

### Post by darkod on 2012-10-06
Hmm, it should have worked.

But the alternate installer not showing the array at all (not having a driver for it I guess) might point you to the issue. It seems it can't recognize it correctly. Which might be why the problem of installing grub2 is present.

In live mode, can you post the output of:
sudo fdisk -l (small L)
sudo parted -l

---

### Post by sgoranov on 2012-10-06
I decided to reinstall ubuntu - just ubuntu (removed Windows) from scratch with default installtion (the install program makde parttions and evrything). Still grub doesn't appear. Below is the result from both commands:

```
# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table
fdisk: unable to seek on /dev/sdb: Invalid argument
root@ubuntu:~# parted -l
Error: /dev/sda: unrecognised disk label                                  

Error: Can't have a partition outside the disk!                           

Model: Kingston DT 100 G2 (scsi)
Disk /dev/sdc: 8010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8010MB  8010MB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ddf1_raid02p1: 1987GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1987GB  1987GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ddf1_raid02p2: 12.9GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End     Size    Type     File system     Flags
 1      1024B  12.9GB  12.9GB  primary  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ddf1_raid02p5: 12.9GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  12.9GB  12.9GB  linux-swap(v1)


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/ddf1_raid02: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      131kB   1987GB  1987GB  primary   ext4
 2      1987GB  2000GB  12.9GB  extended
 5      1987GB  2000GB  12.9GB  logical   linux-swap(v1)



```

Have to note before that I managed to install grub somehow but it still didn't work. Instead I get an error like - "no such disks" or something like that. I was playing with following commands:

grub-install --boot-directory=/mnt/boot/ /dev/sdb
grub-install --boot-directory=/mnt/boot/ /dev/sda

But now this is the result from both:
```
# grub-install --boot-directory=/mnt/boot/ /dev/sdb 
/usr/sbin/grub-setup: warn: out of disk.
/usr/sbin/grub-setup: error: embedding is not possible, but this is required for cross-disk install.
root@ubuntu:~# grub-install --boot-directory=/mnt/boot/ /dev/sda
/usr/sbin/grub-setup: error: unable to identify a filesystem in hd0; safety check can't be performed.

```

---

### Post by darkod on 2012-10-06
That depends on what have you mounted at /mnt. And the bootloader doesn't go to /dev/sda with raid, as already mentioned.

Not sure if it will work, but in this latest situation you would install grub2 with:
```
sudo mount /dev/mapper/ddf1_raid02p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/ddf1_raid02
```

That would mount the current root partition which is p1, and install grub2 to the MBR of the array.

Note: If you are happy using only ubuntu, in that case it's better to delete the fakeraid array and use software raid. What you wrote above about the software bios raid is not exactly true.
We know bios raid is not true hardware raid, hence the term fakeraid.
But in the linux world if you say software raid that means raid made with mdadm, in which case you use partitions that the OS combines in raid arrays. Fakeraid has nothing to do with it. And that's why windows can't install on linux software raid since it can't understand it at all.

---

